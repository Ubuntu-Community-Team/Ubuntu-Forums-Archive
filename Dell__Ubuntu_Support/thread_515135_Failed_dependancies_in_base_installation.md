---
title: "Failed dependancies in base installation"
date: 2007-08-01
forum: Dell  Ubuntu Support
---

### Post by inflamous on 2007-08-01
Hi, I've been trying to install Kubuntu 7.04 on my Dell Inspiron 1501 for the past couple of days.  I have an AMD mobile Sempron 3500+ (64-bit) so I've tried both the x86 and amd64 alternate install cds, but I always get the same error.  I'm putting the Linux and the boot loader on a logical drive, 15gb for Ubuntu, 1gb swap and 8mb for GRUB.

However, everything goes all and good (except the wireless, which I'll have to fix after the installation) until I reach the base installation.  At about 83% I get a "kernel failed to install"-type message and it tells me to check virtual console 4.  That tells me that linux-generic depends on linux-image-generic which is not configured yet.

I decided to change the debconf to a low priority so that I could change the kernel, but all of them fail, except when I choose not to install any kernel.

So I decided that I should find ways to install the kernel later, and tried to install GRUB, which failed...

Does anyone know how I can finish the installation? I'm kinda fed up with trying to install this (I hate being n00b :()

---

### Post by Rocket2DMn on 2007-08-01
Have you tried the alternate cd?  It gives a text based install rather than a live session.
[http://www.kubuntu.org/download.php#latest](http://www.kubuntu.org/download.php#latest) - choose your mirror, then get the -alternate- iso instead of the -desktop-

---

### Post by inflamous on 2007-08-01
Sorry, I forgot to mention that, I am using the alternate install cds
I'm also burning the cds with a slower speed and I've done an integrity check on each cd, and it always says that the cd is fine.

---

### Post by inflamous on 2007-08-02
Just wondering, is it possible to install the kernel and GRUB with Knoppix after installing all the base components and additional software for Kubuntu?

---

### Post by inflamous on 2007-08-05
I fixed the base installation problem, my /boot was too small, so I made it 256 mb, but now when I reach the part where GRUB is supposed to install, it just stays at 0% and I can type things into the virtual console (but nothing happens when I pres enter).

---

