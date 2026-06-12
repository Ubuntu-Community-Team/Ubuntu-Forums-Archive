---
title: "Achieve different CPU loads?"
date: 2008-01-19
forum: Education &amp; Science
---

### Post by tseo on 2008-01-19
Can someone recommend me a way to load up my CPU to 0,25,50,75 and 100%. I need this for a school project cause I need to do a performance test on a database.

I can see the 0 ans 100% but I really don't have any idea about the others.

Any help will be appreciated.

---

### Post by amo-ej1 on 2008-01-19
Well, examine the following piece of C: 

```

#include <unistd.h>
#include <sys/time.h>
#include <time.h>

#define TOTALCYCLE  50000  //!< Total cycle takes this amount of useconds
#define SLEEPCYCLE  45000  //!< Sleep this amount of useconds 

inline wakeUp(struct timeval *start, struct timeval *end)
{
    if(end->tv_sec >  start->tv_sec)
    {
        return 1;
    }
    
    if(end->tv_sec == start->tv_sec && end->tv_usec > start->tv_usec)
    {
        return 1;
    }
    return 0;
}

int main(int arc, char **argv)
{
    
    struct timeval start;
    struct timeval end;
    while(1)
    {
        // Do active wait
        gettimeofday(&start,NULL);
        start.tv_usec+=TOTALCYCLE-SLEEPCYCLE;
        while(start.tv_usec > 1000000)
        {
            start.tv_usec-=1000000;
            start.tv_sec++;
        }
        gettimeofday(&end,NULL);
        while(wakeUp(&start,&end)==0)
        {
            gettimeofday(&end,NULL);
        } 
        
        // Go to sleep 
        usleep(SLEEPCYCLE);
    }
}


```

What does it do ? Well you use the TOTALCYCLE and SLEEPCYCLE #define's to set how long a cycle last. In the example above you have 50.000 microsecond cycles of which we will sleep for 45.000 microseconds. During the 5000 remaining microseconds the application will be very active in polling the kernel to get the time.

Hence a 50000 and 25000 will give you a 50% cpu usage. 50000 and 12500 will give you a 75% cpu load.

Note to test this make sure you don't have any hyperthreading or other active cores (using uniprocessor only). And keep in mind that the cpy load will be rather 'bursty'.  Also don't go below 10msec intervals since then you reach the linux granularity. 

Hope this helps.

---

### Post by tseo on 2008-01-19
Thanks. Definitely going to try this.

---

### Post by Lster on 2008-01-19
I never could of guessed a program that just wasted CPU time could be useful. ;)

---

### Post by ssam on 2008-01-19
you might want to use nice to keep the cpu wasting proc at a near constant level.

---

