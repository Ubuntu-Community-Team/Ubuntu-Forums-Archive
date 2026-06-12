---
title: "problem installing on HP h8-1213"
date: 2012-07-04
forum: Desktop Environments
---

### Post by lbourbeau on 2012-07-04
Just bought a HP H8-1213 and wanted to install Ubuntu 12.04 but after selecting install ubuntu on the installation menu I get a blank screen with a flashing cursor. There's activity in the DVD drive but after a minute it stops and nothing happens.

I want to do a full install, no dual-boot, so I already know the partition issue doesn't affect me.

Please help because I'm really tired of Windows.

---

### Post by msammels on 2012-07-04
Have you tried re-burning the DVD at a slower speed, or copying it to a USB drive instead?

---

### Post by lbourbeau on 2012-07-04
I tried but I always an error right before the Grub style menu : Prefix is not set .
Then I have the following options :
Try Ubuntu without installing
Install Ubuntu
Check disc for defects

I have tried the first 2 but no success. :-(

Please note that I tried with a DVD and/or USB key.

---

### Post by Petro Dawg on 2012-07-04
Does the computer run the live session from the CD?

---

### Post by lbourbeau on 2012-07-04
Not even. Here's the components of the computer :
i7-3770
2Tb Caviar Green HD
16 Gigs of ram
Nvidia GeForce GT 620
El-Cheapo DVD Burner

---

### Post by lbourbeau on 2012-07-04
Found another thread about the same problem. Apparently it's the UEFI thing in the BIOS. trying it right now.
I'll keep you guys posted.

---

### Post by lbourbeau on 2012-07-04
So after desabling UEFI in the BIOS and retrying to install from the DVD, It's another fail for my Ubuntu installation.

Anybody as another idea?

---

### Post by lbourbeau on 2012-07-04
Downloaded the alternative version of Ubuntu 12.04 and installation seems to be working. 

So first you'll need to disable UEFI in your bios.

Then reboot your computer with the DVD drive to install.

You'll need some firmware to use the wlan card. I included the files in the zip file attached to this post.

Thanks everybody for the support and I hope this thread will help more people.

---

### Post by lbourbeau on 2012-07-04
the Installation was a success but when I try to boot I only see weird lines across the screen.

Ideas?

---

### Post by lbourbeau on 2012-07-04
Ah finally, I got it to work. During installation, use those settings nomodeset acpi=off and it should be fine.

Thanks,

---

### Post by claracc on 2012-07-05
As you have fixed your problem, please mark the thread as solved with thread tools in the upper right part of the page, so, other users can find information quicker.

---

