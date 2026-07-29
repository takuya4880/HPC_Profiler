# Copyright (c) 2020 NVIDIA Corporation.  All rights reserved. 

CC := nvc++
NVTX_INC := -I/shared/software/hpc_sdk/Linux_aarch64/26.3/cuda/13.1/targets/sbsa-linux/include
CFLAGS := -O3 -w -ldl $(NVTX_INC)
ACCFLAGS := -acc -gpu=ccnative -Minfo=accel

FC := nvfortran
FFLAGS := -fast
LDFLAGS := -lnvhpcwrapnvtx

miniWeather_c: miniWeather_openacc.cpp
	${CC} ${CFLAGS} ${ACCFLAGS} -o miniWeather miniWeather_openacc.cpp 

miniWeather_f: miniWeather_openacc.f90
	$(FC) $(FFLAGS) $(ACCFLAGS) miniWeather_openacc.f90 -o miniWeather $(LDFLAGS)
    
clean:
	rm -f *.o miniWeather *.nsys-rep *.sqlite *.ncu-rep
