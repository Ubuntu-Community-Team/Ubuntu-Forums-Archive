---
title: "Completely Lost"
date: 2005-07-07
forum: Desktop Environments
---

### Post by CaptnDan on 2005-07-07
Hi,

Sorry, I'm really new to Linux. I've wanted to get into it for a long time, but only recently discovered the idea of a "Live CD", to test it all out first.

I downloaded the Kubuntu Live CD iso, and burnt it to CD. I booted it up, and it went through the various setups etc.

Eventually it comes to a promt saying something like "ubuntu@ubuntu: ~$", and it this point I become completely lost. It's not the GUI referred to in the FAQ's and guides I've read.

What should I do at this point?

Sorry, if this is really obvious...

Thanks in advance..

---

### Post by alastair on 2005-07-07
Sounds like the GUI/X has not started. Assuming you are at some sort of shell prompt. There might have been a problem with configuring the GUI.

If you feel brave :

The GUI config file is :

/etc/X11/xorg.conf

and the GUI log file (errors etc.) is :

/var/log/Xorg.0.log

If you could copy these and post, perhaps we could help. Please mention what graphics card you have.

---

### Post by CaptnDan on 2005-07-07
Sorry again, I'm unsure..

How do I get to open those files if, using the Live CD, everything is only stored temporarily? From that promp, I don't have any software that can open these files do I?

I'm using a GeForce4 MX 440 PCI.

Oh, I do get "ror: temporary failure in name resolution" failing when it begins.

Could this be a reason for the problem?

Thanks again

 ](*,)

---

### Post by black hole sun on 2005-07-08
Type "startx" (without quotes) at the prompt ;)

---

### Post by CaptnDan on 2005-07-08
Thank you both :)

I now have the error message "no screens found". I've read about fixes for this, but how can you edit your settings from this command screen?

---

### Post by alastair on 2005-07-08
Yes - persistence in a Live CD. The eternal problem :-)

You need to get the files :

/var/log/Xorg.0.log
/etc/X11/xorg.conf

to a persistent medium. Do you have a USB stick? Or floppy? Some way to save them and post them?

Even from a text console, you can log in multiple times by using CTRL+ALT+F1(-F12)

On another console (CTRL+ALT+F2 say), you can log in then :

sudo sudo tail -f /var/log/syslog

Plug in a USB stick - see what device is allocated e.g. /dev/sda1, then 

Return to first console (CTRL+ALT+F1, say), and :

sudo mkdir /mnt/tmp
sudo mount /dev/sda1 /mnt/tmp

sudo cp /var/log/Xorg.0.log /mnt/tmp
sudo cp /etc/X11/xorg.conf /mnt/tmp

sudo umount /mnt/tmp

Then get to an OS (e.g. XP) that you can get to the USB stick and copy the files, then post.

---

### Post by CaptnDan on 2005-07-10
Thanks for all your help. :) But I've started using Slax now, and it seems to be running fine.

---

### Post by sooqing on 2005-07-10
something is defintely wrong without it starting x.. hold on installing linux till ur resolved ur problem..

---

