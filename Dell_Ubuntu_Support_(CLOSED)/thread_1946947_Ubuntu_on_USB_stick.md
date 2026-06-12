---
title: "Ubuntu on USB stick"
date: 2012-03-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by girish53 on 2012-03-25
Today I created a USB stick with ubuntu desktop on it, and was able to boot my dell dimension 92000 using it. But I could not find some of the familiar things. For example, I could not open a terminal. 

I have a 8 GB USB stick. There is enough room, I think, to install my Linux applications on it. As I understand it, I should be able to use my PC like a Linux box with 8 GB hard drive, right? Does this ubuntu have compilers (C, Fortran) and X11? I have gnome in the past, but this desktop has a lot of things missing. Did I get the right Ubuntu (11.04) for the right purpose? There were several choices there. Please advise.

Thanks much.
Girish Joglekar

---

### Post by gbrainin on 2012-03-25
First of all, 8GB should be more than adequate for this purpose.  I think the minimum requirement is still more like 2.

However, depending on how you created the USB stick, there may or may not be (or be enough) "persistent" storage set up to keep track of your settings, saved files, etc.  What program did you use to create the stick?

As for software, I'm not sure exactly what comes with the default distribution anymore, but anything that isn't there can easily be downloaded through the software center (or whatever they're calling it these days).  X11 I assume you have if you're successfully booting into a graphical interface; C and Fortran compilers probably aren't already included, but again, can be added easily.

I would think a terminal emulator would be in there somewhere, but even if it isn't you can always switch to a full-screen terminal (Ctrl-Alt-F1 through -F6 are 6 different terminals, Ctrl-Alt-F7 takes you back to the GUI).

---

### Post by girish53 on 2012-03-26
> **gbrainin said:**
> First of all, 8GB should be more than adequate for this purpose.  I think the minimum requirement is still more like 2.

However, depending on how you created the USB stick, there may or may not be (or be enough) "persistent" storage set up to keep track of your settings, saved files, etc.  What program did you use to create the stick?

As for software, I'm not sure exactly what comes with the default distribution anymore, but anything that isn't there can easily be downloaded through the software center (or whatever they're calling it these days).  X11 I assume you have if you're successfully booting into a graphical interface; C and Fortran compilers probably aren't already included, but again, can be added easily.

I would think a terminal emulator would be in there somewhere, but even if it isn't you can always switch to a full-screen terminal (Ctrl-Alt-F1 through -F6 are 6 different terminals, Ctrl-Alt-F7 takes you back to the GUI).
Thanks much. I will try your suggestion later today (this is my spare time hobby). I used the ubuntu website download -> cd/usb -> ubuntu desktop 11.04. Then it asked me to download an iso and pick the drive for my usb. That was it. Then I rebooted my PC. What is the diff bet desktop and studio? That was another possibility. 
Girish

---

### Post by gbrainin on 2012-03-26
Scanning quickly through the instructions, it appears that what you're creating is a USB version of the "live CD."  What that means is that you can boot from it, and run it (note that it'll be substantially slower than a hard drive install), but the file system is in RAM.  In other words, it won't remember things (like additional programs you've installed) the next time you boot.

It is possible to create a USB drive with this capability.  See instructions for multiple methods to do so here: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

I am not familiar with the "studio" version, but like most variants, it's probably just a slightly different collection of default programs, possibly with a different desktop, etc.  The underlying operating system is the same.

---

### Post by girish53 on 2012-03-26
> **gbrainin said:**
> Scanning quickly through the instructions, it appears that what you're creating is a USB version of the "live CD."  What that means is that you can boot from it, and run it (note that it'll be substantially slower than a hard drive install), but the file system is in RAM.  In other words, it won't remember things (like additional programs you've installed) the next time you boot.

It is possible to create a USB drive with this capability.  See instructions for multiple methods to do so here: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

I am not familiar with the "studio" version, but like most variants, it's probably just a slightly different collection of default programs, possibly with a different desktop, etc.  The underlying operating system is the same.
Thank you for the link. A quick glance looks promising. I will explore it later. 
Girish

---

