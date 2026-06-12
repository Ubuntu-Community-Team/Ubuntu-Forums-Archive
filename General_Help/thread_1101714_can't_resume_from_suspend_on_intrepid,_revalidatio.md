---
title: "can't resume from suspend on intrepid, revalidation failed &amp; I/O errors"
date: 2009-03-20
forum: General Help
---

### Post by gotoman00 on 2009-03-20
hello, i seem to have a serious problem coming out of suspend.

currently running on intrepid mini with no gdm, using asus M3N78-EM mobo w/ integrated nvidia geforce 8300 and amd athlon x2+ 7700, booting from a sata hd... currently using as an htpc and it boots directly into xbmc... i used this guide to help install it:

[http://xbmc.org/wiki/?title=HOW-TO_i...)_step-by-step](http://xbmc.org/wiki/?title=HOW-TO_i...)_step-by-step)

everything seems to run smoothly, i have an mce remote and that works as well, and goes into suspend mode fine... even the power button on the mce remote will wake it.... however once i resume i get a black screen with blinking cursor for about 30 seconds, then quickly flashes 3 or 4 lines saying 'revalidation failed'... xbmc then pops up after, however it's only running from memory and trying to navigate menus further kills xbmc and x completely and i get a coulple of lines of errors:

"/home/xbmc/.xsession: Read-only file system"

followed by

"chown: changing ownership of '/home/xbmc/.xsession': Read-only file system"

and this will continue till i hard reboot... and right before it does i get dev sda I/O errors as well...

i've tried S1, S3 and auto in my bios for power settings, disabling/enabling apci 2....nothing seems to work... i'm doomed from being able to suspend...

after booting, suspending, trying to resume, doing a hard shut down, and rebooting, this is what i've got in dmesg and messages... not too linux savvy myself yet so here are links to each:

[http://halo.anarchic-x.net/gotoman/messages](http://halo.anarchic-x.net/gotoman/messages)

[http://halo.anarchic-x.net/gotoman/dmesg](http://halo.anarchic-x.net/gotoman/dmesg)

please help!

---

### Post by gotoman00 on 2009-03-21
bump?

---

### Post by hypocratus on 2009-03-21
Looking at that wiki entry, did you make sure that the user you are using for XBMC is xbmc? Otherwise you have to alter the PolicyKit config file you downloaded to change the user name.

---

### Post by gotoman00 on 2009-03-21
yup, same user... pretty sure it has nothing to do with xbmc, i even posted in their forums and they said that most likely it was an ubuntu problem.... seems my sata controller isn't coming back and i dont know why or how to fix it :(

---

### Post by gotoman00 on 2009-03-21
update: this time i did a normal hardy install with gdm, installed the new nvidia drivers, and tried suspend from gnome and im still getting the same errors.  :(

---

### Post by Murz on 2009-05-21
Confirm this error on Kubuntu 9.04: after S3 suspend computer wakes up normally, I see the mouse pointer, windows, etc; but the system can't read from the HDD drive (/dev/sda). After some time I see the errors reading from the drive. After pressing reset all goes to work good.
I try the AHCI and SATA modes on the bios, enable/disable AHCI 2.0, upgrade bios to latest version, but no one thing helps.
What I can try nextly for solve this problem?

---

### Post by Murz on 2009-05-21
I have found an active bug in launchpad about this problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350449](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350449)

---

