---
title: "RAM upgrade did not reflected in Ubuntu 10.04"
date: 2012-01-21
forum: Desktop Environments
---

### Post by narayanab16 on 2012-01-21
Hi GoodEvening,

I have upgraded my system RAM from 4GB to 8GB today i.e 21/01/2011.
I have gone to System->Administartion-> System Monitor where i can see still my 4 GB only.

How to get my 8GB RAM to my ubuntu 10.04 desktop version

Kindly help its urgent

---

### Post by mcduck on 2012-01-21
Does that new RAM show correctly in BIOS? And are you running 32- or 64-bit version of Ubuntu?

If you are running 64-bit version and the memory appears to be detected correctly in BIOS, try running the memtest from Grub menu (or Ubuntu CD).

---

### Post by IRQsRFun on 2012-01-21
My guess is that you will have to upgrade to a 64 bit operating system.  All 32 bit operating systems that I am aware of use a 32 bit virtual address space (2^32 = 4294967296 == 4G(i)B ).  This is true for 32 bit versions of windows as well.  I too am limited to 4 gig of ram usage on Ubuntu 10.04 LTS

---

### Post by narayanab16 on 2012-01-21
Thanks for your reply.

I have done memory test where i can see 8gb ram.
i dont know how to check 32 or 64 bit ubuntu 10.04.2
Please help commands to check OS version, how to reflect 8gb into my ubuntu

---

### Post by jerrrys on 2012-01-21
in terminal

cat /proc/meminfo | grep MemTotal

also

uname -m

---

### Post by narayanab16 on 2012-01-21
here is the output:

narayana@narayana-ubuntu:~$ cat /proc/meminfo | grep MemTotal
MemTotal:        3402376 kB
narayana@narayana-ubuntu:~$ uname -m
i686

---

### Post by 2F4U on 2012-01-21
You are on 32 bit which recognizes by default only 4 GB of RAM.

---

### Post by jerrrys on 2012-01-21
If you wish to stay with 32 bit and use the extra ram, you need to...

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=install+pae+kernel&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=install+pae+kernel&sa=Search&cof=FORID:9)

---

### Post by narayanab16 on 2012-01-21
Thanks for your reply

i would like to continue with 32 bit , let me check the link and get back to the forum if i find any issues

---

### Post by jerrrys on 2012-01-21
Should be painless, but keep a couple of beers handy just in case :D

Good luck and welcome to the forum.

---

### Post by narayanab16 on 2012-01-24
Thanks for your quick help.
 
I have 8 gb ram and upgraded to ubuntu 11.10.
 
Kindly deffer this query from forum, i dont know how to use effectively this forum.
 
Thanks

---

### Post by narayanab16 on 2012-01-24
Thanks for your quick help.

I have 8 gb ram and upgraded to ubuntu 11.10.

Kindly deffer this query from forum, i dont know how to use effectively this forum.

Thanks

---

