---
title: "I Just Bought a Dell Studio 1555 - Any Tips?"
date: 2010-03-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arcelios on 2010-03-28
I just took the plunge and bought myself a new computer to replace my aging MacBook. Here are the specs:

**Model:** Dell Studio 1555
**Processor:** Intel Core i5-520M (2.40 GHz)
**RAM:** 4GB
**Graphics Card:** ATI Mobility Radeon HD 4570, 512MB
**Wireless:** Intel Centrino Advanced-N 6200
**Hard Drive:** 320GB SATA Hard Drive (7200RPM)
**OS:** Windows 7 64-bit (_going to install Ubuntu_)

I won't be getting it 'till ~April 20th.

Does anyone have any tips for running Ubuntu on a computer like this? Should I use 64-bit Ubuntu on this? What version of Ubuntu should I use? Will I have to tweak any settings to get it to work (wireless, graphics, etc.)? Any other tips?

Thanks in advance

---

### Post by garok89 on 2010-03-28
Id say, if you want things to work that much smoother without any extra work (flash etc) then go 32bit. if you want to make full use of your system and you do AV processing, then go 64bit

i wrote this little guide that applies to Karmic (and for the most part Lucid)

in lucid you dont need to the the "noapic" thing in grub to get everything working, but you do in karmic

also in the guide is the easy way to get graphics and wireless working
in lucid, for wireless, one of the packages isnt in the repos, just install the other one and it should be fine

[http://ubuntuforums.org/showthread.php?t=1412593](http://ubuntuforums.org/showthread.php?t=1412593)

EDIT: since it has the intel wireless instead of broadcomm (my older 1555 has the broadcomm) you shouldnt need to do the bcmwl stuff

---

### Post by waynefoutz on 2010-03-28
I agree on the 32 bit version. You're good on the video driver, for now anyway. ATI doesn't support their card with Linux for very long, so I don't recommend them and prefer Nvida.  But your good for a while.  You can get the driver here: [http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx") 
The open source driver may get the job done, and I'd try that first. But if not, get the one at the link above. My personal litmus test is Google Earth. If that runs correctly, then you're done fussing with video drivers, and it will run everything to throw at it. 

As for Wi-Fi, almost every Dell I've installed Ubuntu on I've had to plug it up to the router with a hard wire so it could download the Broadcom STA driver. You may run into a similar problem with the Intel. Not a big deal, just make sure you have an ethernet cable handy after you install.

---

### Post by garok89 on 2010-03-28
the open source driver crashed mine every time i closed the screen so had to use the fglrx one
hopefully both the proprietary and opensource will be perfect by the time you get it

---

### Post by arcelios on 2010-03-29
> **waynefoutz said:**
> I agree on the 32 bit version. You're good on the video driver, for now anyway. ATI doesn't support their card with Linux for very long, so I don't recommend them and prefer Nvida.  But your good for a while.  You can get the driver here: [http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx") 
The open source driver may get the job done, and I'd try that first. But if not, get the one at the link above. My personal litmus test is Google Earth. If that runs correctly, then you're done fussing with video drivers, and it will run everything to throw at it. 

As for Wi-Fi, almost every Dell I've installed Ubuntu on I've had to plug it up to the router with a hard wire so it could download the Broadcom STA driver. You may run into a similar problem with the Intel. Not a big deal, just make sure you have an ethernet cable handy after you install.

Okay, thanks. I'll go with the 32-bit version for now; maybe install 64-bit further down the line.

Does anyone have any suggestions as far as version? Would 9.10 work all right, or should I use 9.04/10.04?

---

### Post by garok89 on 2010-03-29
10.04
even as a beta its pretty damn stable....upon release it will kick ***

---

### Post by arcelios on 2010-03-30
> **garok89 said:**
> 10.04
even as a beta its pretty damn stable....upon release it will kick ***

Thanks. I had read somewhere that the Studio 1555 display/graphics card worked better in 10.04 than in 9.10.

---

### Post by garok89 on 2010-03-30
the opensource one is almost perfect....only issue i have is that closing the lid causes it to crash
so im using the ATI one...only issue being plymouth looks crap

---

