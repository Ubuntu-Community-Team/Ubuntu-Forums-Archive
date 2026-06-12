---
title: "Vostro 1310 Ubuntu 8.04. Webcam, Google Earth,..."
date: 2008-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by keryonic on 2008-05-10
Hi,

I didn't want Vista so I installed Ubuntu Hardy Heron. It works but I have spent hours troubleshooting each time I install something new.

Two main problems remains:

1. The webcam was working at the begining without any change to the configuration. Then I tried to install a DVB TV USB stick without any success, I also load the nvidia driver but now the webcam doesn't work. I spent hours looking for a solution but nothing (I am a total noob).

2. Google Earth works just after a fresh install but if I close it and reopen it, the globe has disapeared. I guess it is a problem with nvidia.

I have moved /home to a new partition and, if I don't find solution for 1, I would like to reinstall Ubuntu but I don't know how it behaves (I know Windows not Linux). Will I mess Grub? Will I have to reinstall all the programs? Is it easy?

I would appreciate any help. Tx

---

### Post by keryonic on 2008-05-11
I found the solution with Google Earth installing it directly from the Medibuntu repository. Medibuntu helped me also with codecs needed for DVD reading.

The webcam:
Ubuntu 8.04 can be booted with 2.6.24-12 generic or 2.6.24-16 generic kernel. I am a total noob and I don't understand what is the difference but I noticed that if I boot with the 2.6.24-12-generic kernel, the webcam works perfectly!! 

What should I do to make it work also with 2.6.24.-16?

---

### Post by aikiwolfie on 2008-05-11
The new version of GoogleEarth didn't work for me eithers. I just reinstalled the old version. I'm not sure what's going on with your web cam. But try installing cheese. That's the Gnome web cam application. It works great for me.

---

### Post by keryonic on 2008-05-12
I have also installed the old Google Earth version.

Thanks to try to help me with the webcam but I had already installed Cheese and it works...with the other kernel (the one that ends with -12) and it worked on kernel 16 also with live disk and before I screwed with a DVB TV driver.

It is so frustrating because I have everything inside my computer to make it work. I guess I "only" need to recompile the kernel with the right driver. But I am a total noob and will never be able to do it alone.

---

### Post by phux on 2008-05-27
Hmm, the WLAN works for you? I cannot connect to any WLAN somehow... hope i can fix this.

---

### Post by keryonic on 2008-05-27
Wlan worked for me out of the box. I use it with a WEP encrypted network (I have heard there are some problems with WPA but I don't use it anyway).

Wlan worked for me with the live CD. Are you sure you have the latest Hardy Heron version? (A lot of beta were circulating before official release).

Good luck.

---

### Post by keryonic on 2008-05-27
Does the mic works for you? I am becoming crazy looking for a solution!

Everything else works for me. (Maybe suspend/hibernate problems but I never use it). But since I am a complete noob, I can tell you I passed by a lot of frustrations.

---

### Post by phux on 2008-05-28
... then it might be the WPA-Problem.
I will connect via LAN and update everything. Hopefully the driver will do the magic.

I installed wubi, its awesome :-)

---

### Post by phux on 2008-05-31
The Problem was:
Wubi downloaded the 64bit-version of Ubuntu...
There seems to be (as always) a driver-problem.
I fixed this by manually downloading the 32bit-version and placing it in the same directory with the wubi.exe.
Not everything runs fine.

Greetings,
Michael

---

### Post by dppowell on 2008-05-31
> **keryonic said:**
> I found the solution with Google Earth installing it directly from the Medibuntu repository.

I also used the Medibuntu .deb, but I get the "no globe" problem unless I run the app through sudo (i.e., as root).  I'm hoping that's not a permanent workaround. :-|

---

### Post by umayado on 2008-06-20
same problem here, only using sudo makes it work

---

