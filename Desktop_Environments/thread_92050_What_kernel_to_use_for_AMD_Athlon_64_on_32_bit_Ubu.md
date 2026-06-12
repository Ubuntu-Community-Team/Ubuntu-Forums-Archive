---
title: "What kernel to use for AMD Athlon 64 on 32 bit Ubuntu?"
date: 2005-11-18
forum: Desktop Environments
---

### Post by anton123 on 2005-11-18
Hello to all,

I have recently bought a PC with an AMD 64  processor. Ubuntu 5.10 CD comes with the 386 kernel. Using Synaptic, I can get the 686 kernel as well as the K7 kernel. However, I don't know which one of the two to get so that I get the most possible performance from a 32 bit install of Ubuntu on a 64 processor. I tried the version of Ubuntu for AMD64 but I chose to stick with the 32 bit version for now. So, should I get the 686 or k7 kernel?

Also, another question. When installing Ubuntu, should I use ext3 or reiserfs 3.6? I have read some comparisons in between the two file systems but the tutorials have ended up in creating more confusion than clarity. Can I get detailed information on advatanges/disadvanatges of using either one of the file systems? Also, will there be an ext4 file system? I heard that it is under works and should outperform reiserfs 4. Can anyone confirm that?

Thank you

---

### Post by Joey French on 2005-11-18
I use the k7 kernel on ubuntu 32, running on Athlon 64. No problems, but you may have to immediately remove powernowd. Don't know why, but it has locked up my box many times.Remove it, no troubles.

---

### Post by anton123 on 2005-11-18
Hi, I see. Does 686 kernel outperform k7 kernel or should I go for the k7 series? Is the k7 series also compatible with Athlon XP which might be the closest to Athlon 64 (except that it is a 32 bit only kernel)?

---

### Post by mcduck on 2005-11-18
No, K7 is better. It does everything 686-kernel does plus some special tricks only available with AMD/Athlon CPUs. Altough I doubt anyone would really notice any difference ;)

686 is for P3/Athlon and newer CPUs by both Intel and AMD. K7 is for Athlon and newer AMD CPUs.

---

### Post by garciadc on 2005-11-18
I use k8 kernel for my amd64 processor

---

### Post by Mr.Mechano on 2006-06-23
I have Dapper 32bit on Turion 64 ML-28. I use it on a desktop machine that is my home server also, and using frequency scaling the CPU can be used at 800Mhz and I can save near 12kwatt a year only from CPU power consumption. 

I prefer to use 32bit kernel because I use it like a desktop machine and need video codecs, flash plugin and other stuffs to work.

The CPU has frequency scaling from 800 to 1600Mhz. 
With stock 386 kernel the powernowd daemon works.
But with both K7 and 686 kernel the CPU stays always at 1600Mhz.

How to make frequency scaling work with 686 and K7 kernels?

---

### Post by Paulo Wageck on 2006-07-19
can the athlon 66 4000+ use the k7-smp? or should I stick with the regular k7?

---

### Post by moffa on 2006-07-31
smp is made for multiple cores.  If you have a dual core cpu like the X2 then you should use the smp kernel.  If you just have the single core chip then just use the regular k7 kernel.

---

