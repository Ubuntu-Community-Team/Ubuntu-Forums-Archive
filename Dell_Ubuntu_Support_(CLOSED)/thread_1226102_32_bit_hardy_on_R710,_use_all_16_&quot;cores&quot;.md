---
title: "32 bit hardy on R710, use all 16 &quot;cores&quot;"
date: 2009-07-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hlynur on 2009-07-29
I have some DELL R710 which comes with a 2 quad core processors and hyperthreading. In total this makes up 16 logical processors. With 64bit ubuntu 8.04 this works fine where the kernel default max cpu is set at 64 processors. 

However the 32 bit default value is 8 processor. Runnig this kernel i get the same performance as removing one of the quad core processors, so not realy good. 

Anyway I have build a custom kernel setting the max cpu to 16 and 64 processor. However this results in a kernel panic just after the 16th processor is brought up. 

Anyone been messing with at R710 as well?

Cheers / Thor

---

### Post by hlynur on 2009-07-30
I fixed the problem by upgrading to a vanilla 2.6.30.3 kernel.
I havn't read the changelog details but there is a new option in this kernel (I havent seen in < 2.6.29 )

[*] Support for big SMP systems with more than 8 CPUs 
then setting the old option
16 Maximum number of CPUs 
to 16 and we are running with 16 logical processor :-)

Cheers / Thor 

BTW There was some minor tease with the bnx2 firmware for the bnx2 driver so i compiled it as well statically into the kernel. 
 Device Drivers  --->
 --- Network device support ->
       Ethernet (1000 Mbit)  ---
<*>   Broadcom NetXtremeII support

and XEN was also giving some problems so i disabled 
Processor type and features  ---> 
[ ] Paravirtualized guest support  --->

---

