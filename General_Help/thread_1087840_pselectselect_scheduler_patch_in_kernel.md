---
title: "pselect/select scheduler patch in kernel?"
date: 2009-03-05
forum: General Help
---

### Post by zzaappp on 2009-03-05
I noticed that the default ubuntu kernel is using the default scheduler for pselect and select.  

With select the metric going into the function call can have a granularity down into the microseconds.  And with pselect, the granularity is in nanoseconds.

The issue is that the default scheduler is actually in milliseconds.

There used to be one or more patches available to make the select and pselect schedulers considerably better.  

I have tried both the desktop and server versions of ubuntu and can see that neither of them have the select/pselect scheduler patches in place.  On the other hand, I have seen that there are other kernels available in ubuntu, and I was hoping someone could tell me if they know of an available kernel that would have the patch.

To prove the performance of the select/pselect patch, I use the following program:

```
#include <stdlib.h>
#include <stdio.h>
#include <string.h>

#include <sys/time.h>
#include <sys/timeb.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/times.h>
#include <signal.h>

#include <errno.h>

unsigned long milsec(void)
{
  struct timeval  tv;
  struct timezone tz;

  if( gettimeofday( &tv,&tz ) == -1 )
    return( 0 );
  return( tv.tv_usec + (tv.tv_sec*1000*1000));
}

const char* uname(void)
{
  static char  buff[1024];
  FILE* fp=fopen("/proc/version","r");

  if( fp==NULL )
    return( "(OS unknown)" );

  fgets(buff,sizeof(buff),fp);
  buff[strlen(buff)-1] = 0;
  return( buff );
}

int main(int argc,char *argv[])
{
  volatile char           B1[102400];
  volatile char           B2[102400];
  volatile unsigned long  Start,Stop;
  volatile int            count,max=1000,index;
  struct timeval          tv;
  struct timespec         tvp;

  if( argc >=2 ) 
    max = atoi(argv[1]);

  printf("OS:  %s\n",uname());
  Start = milsec();
  for(count=0; count<max; ++count)
  {
    tv.tv_sec  = 0;
    tv.tv_usec = 1;
    select(0,NULL,NULL,NULL,&tv);
  }
  Stop  = milsec();
  printf("TICK  :  Iterations[%d] Delta[%10lu] Avg[%7.3f]\n",max,Stop-Start,(double)(Stop-Start)/(double)(max));

  Start = milsec();
  for(count=0; count<max; ++count)
  {
    tvp.tv_sec  = 0;
    tvp.tv_nsec = 1;
    pselect(0,NULL,NULL,NULL,&tvp,NULL);
  }
  Stop  = milsec();
  printf("TICKp :  Iterations[%d] Delta[%10lu] Avg[%7.3f]\n",max,Stop-Start,(double)(Stop-Start)/(double)(max));

  ////////////////////////////////////////
  // BENCH of memcpy/indexing
  ////////////////////////////////////////
  
  Start = milsec();
  for(count=0; count<max; ++count)
  {
    for(index=0; index<sizeof(B1); ++index)
      B2[index] = B1[index];
  }
  Stop  = milsec();
  printf("MEMCPY:  Iterations[%d] Delta[%10lu] Avg[%7.3f]\n",max,Stop-Start,(double)(Stop-Start)/(double)(max));
}

```

To run the test, save this file as "ticks.c", then use the following example:
```

$ gcc -o ticks -O0 ticks.c
$ ./ticks
OS:  Linux version 2.6.27-11-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:28:32 UTC 2009
TICK  :  Iterations[1000] Delta[   4001182] Avg[4001.182]
TICKp :  Iterations[1000] Delta[   4003757] Avg[4003.757]
MEMCPY:  Iterations[1000] Delta[    563401] Avg[563.401]

```

This run is on my local computer.  Now here's an example from a different distro which contains the pselect scheduler patch (but not the select patch):
```

OS:  Linux version 2.6.16.60-0.21-smp (geeko@buildhost) (gcc version 4.1.2 20070115 (SUSE Linux)) #1 SMP Tue May 6 12:41:02 UTC 2008
TICK  :  Iterations[1000] Delta[   3998045] Avg[3998.045]
TICKp :  Iterations[1000] Delta[       338] Avg[  0.338]
MEMCPY:  Iterations[1000] Delta[    239220] Avg[239.220]

```
You can clearly see the difference:  pselect is responding as it should because the scheduler patch is in place.


Since I have to manage multiple machines, I would much rather have a standard ubuntu kernel to install.  That would keep me from having to go to each machine, install source, patch it, build it, test it, repeat until stable. 

Does anyone know if one of the kernels has the pselect scheduler patch?

Many thanks

-z

---

### Post by kanikilu on 2009-03-05
Sorry I can't offer something more constructive, but holy crap, if this is "Absolute Beginner Talk", I'm in the wrong forum! :shock:

---

### Post by bapoumba on 2009-03-05
Moved to General Help.

---

