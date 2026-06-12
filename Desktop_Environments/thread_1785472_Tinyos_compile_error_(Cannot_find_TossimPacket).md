---
title: "Tinyos compile error (Cannot find TossimPacket)"
date: 2011-06-18
forum: Desktop Environments
---

### Post by PabloToni on 2011-06-18
I have recently installed Tinyos-2.1.1 on ubuntu 11.04.  In trying to compile a program that had been previously developed on another Tinyos environment using make micaz sim, the following output is seen:
---------------------------------------------------------------------------------------------------------------------
mkdir -p simbuild/micaz
  placing object files in simbuild/micaz
  writing XML schema to app.xml
  compiling TestCommAppC to object file sim.o
ncc -c -shared -fPIC -o simbuild/micaz/sim.o -g -O0 -tossim -fnesc-nido-tosnodes=1000 -fnesc-simulate -fnesc-nido-motenumber=sim_node\(\) -fnesc-gcc=gcc -Wall -Wshadow -Wnesc-all -target=micaz -fnesc-cfile=simbuild/micaz/app.c -board=micasb -DDEFINED_TOS_AM_GROUP=0x22 --param max-inline-insns-single=100000 -DIDENT_APPNAME=\"TestCommAppC\" -DIDENT_USERNAME=\"paul\" -DIDENT_HOSTNAME=\"ubuntu-VirtualB\" -DIDENT_USERHASH=0x9a178cdeL -DIDENT_TIMESTAMP=0x4df8713eL -DIDENT_UIDHASH=0x521274b4L -Wno-nesc-data-race TestCommAppC.nc   -fnesc-dump=components -fnesc-dump=variables -fnesc-dump=constants -fnesc-dump=typedefs -fnesc-dump=interfacedefs -fnesc-dump=tags -fnesc-dumpfile=app.xml
In component `TestCommAppC':
TestCommAppC.nc:66: cannot find `TossimPacket'
make: *** [sim-exe] Error 1
----------------------------------------------------------------------------------------------------------------
Any suggestions on how this could be resolved?

Let me just state some of the things that I have been trying.
1. made sure that python libraries are up to date, and setting the version in the sim.extra file
2. installed older versions of TinyOs (2.1.0 and 2.0.2) 
3. removed and re-installed build-essential (as based on the output, I believe the compile crashes when trying to compile the c code).

Note that the program compiles and runs on a different machine, so something is off with this environment.

Thanks in advance!!!

---

