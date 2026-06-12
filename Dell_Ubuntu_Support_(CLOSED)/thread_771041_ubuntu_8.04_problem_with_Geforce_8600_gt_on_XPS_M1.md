---
title: "ubuntu 8.04 problem with Geforce 8600 gt on XPS M1530"
date: 2008-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 4minab on 2008-04-27
ubuntu 8.04 problem with Geforce 8600 gt on XPS M1530

i install new ubuntu 8.04 64bit

and i have problem with my Video Card

 

when i install driver ([http://www.nvidia.com/object/linux_display_amd64_171.06.01.html](http://www.nvidia.com/object/linux_display_amd64_171.06.01.html)) 

after reboot Gdm , my screen go WITHE , i tryed many ways :mansad:

what is the Problem and solution ?

please Help me !

---

### Post by 4minab on 2008-04-27
?????!!!!!

---

### Post by kklepack on 2008-04-27
I have 1530 with 8600 and I installed 8.04 with wubi and everything is working fine with video card/

?????

---

### Post by Wubuntish on 2008-04-28
There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/208718") for this issue. That driver does not yet work with the newest kernel and the Geforce 8600MGT / 8400MGS. The [beta driver]("http://www.nvidia.com/object/linux_display_amd64_173.08.html") however works. I haven't tested the x64 driver yet, but I expect it to work just fine.

Btw, are you sure you have a amd64? I did not see that option when I bought my M1530.

---

### Post by jespdj on 2008-04-28
Please don't crosspost!

Read my answer in [your other thread]("http://ubuntuforums.org/showthread.php?t=771044").

> **Wubuntish said:**
> There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/208718") for this issue. That driver does not yet work with the newest kernel and the Geforce 8600MGT / 8400MGS.
I am using 64-bit Ubuntu 8.04 and don't have that problem on my XPS M1530 with 8600M GT - the driver works without a white screen of death.

> **Wubuntish said:**
> Btw, are you sure you have a amd64? I did not see that option when I bought my M1530.
Intel Core 2 Duo processors are AMD64 compatible.

---

### Post by xtracool_protik on 2008-05-12
Well I've XPS1530 with Intel core 2 duo 32bit, NVIDIA8400 GS,1280x800 screen When I tried to install NVIDIA driver with ENVYNG at first it was - after reboot I used to get white screen with black strip in the middle then I reinstalled ubuntu and this time tried with synaptic package manager I get display but 800x600 max resolution What can be the problem?

---

