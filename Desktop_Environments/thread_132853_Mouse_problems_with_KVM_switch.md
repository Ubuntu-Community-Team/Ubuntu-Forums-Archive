---
title: "Mouse problems with KVM switch"
date: 2006-02-19
forum: Desktop Environments
---

### Post by khateeb on 2006-02-19
I am using three computers sharing one set of peripherals thru a KVM switch. Only one of them has ubuntu installed. everything works well when the ubuntu machine works alone. However, when i switch to another machine and back, the mouse seems to lose synch and starts acting funny (jump around the screen and causes random right and left clicks) nothing happens when i don't move the mouse though.

Is there any configuration that needs to be done for the mouse to work correctly?

---

### Post by wjp.reg on 2006-02-19
I've been using a KVM switch between a windowsXP and linux box running 64-bit ubuntu 6.4 and Suse 10.0 with no problems or special conifgurations.  Once in a while I might lose the mouse or keyboard, but I only have to re-seat the connections in the KVM for it to operate properly.  My KVM uses PS/2 connections and I use a USB corded infrared MS Mouse with the green PS/2 adapter installed.

What kind of mouse are you using and are they setup with the correct drivers on all 3 machines?

You wouldn't ahppen to be using a laptop ?  I've had the problem you described with my Toshiba where the built-in mouse and external mouse could not be active at the same time.

---

### Post by mauro007 on 2006-08-03
I'm having the same problems with mouse acting crazy after a while.
I have a Celeron a 663 Mhz and 512 mb ram with a S3 Virge graphic card (very basic). the other system is a win2k, both systems are linked via a 2 ports kvm switch.
After a while I'm using Ubuntu, the mouse acts with a mind on its own if I move it and it moves around the screen and switches applications at random. Nothing happens if I don't use the mouse, this also happens if I close all programs, terminals, streamtuner, etc. It's driving me nuts.

Previously I installed Xubuntu running xfce first and kde after install, with the same problems.
With ubuntu, it seams it acts bersek after the latest updates (but I'm not completely sure).
I also intalled the win32 codecs, java and flash plugin and few basic codecs for multimedia.
Can someone please help or pointing me to some other thread where a solution has been found.
One more thing: I have installed Ubuntu using Reiserfs filesystem (same as Xubuntu), should I reintall it using ext3 instead?
Thanks

---

### Post by Stew2 on 2006-08-03
Most KVM switches have a scanning feature that can go crazy when switching between two or more computers. My switch does exactly the same thing occasionaly but I can set my switch to rescan by pressing scroll lock twice (switch beeps) and then hitting "m" (switch beeps again) wait a few moments while the switch rescans and then it is good to go. No more jumpy cursor opening random windows. My switch is a D-Link DKVM-2K. Check your switch manual to see if it has a similiar "rescan" function. :) 
Hope this helps.

Regards,
Stew2

---

### Post by em3raldxiii on 2006-08-04
Yup, I had/have the same problem.  I have two solutions that work:  First, you can unplug and replug the mouse from the switch, works find.  Second, you can rescan as suggested.  Mine uses scroll-lock twice + S to do so, and voila, no more gimpy mouse.
 
There's another thread somewhere about this too ... I'll see if I can find it.  It suggests making a change when your system boots that prevents it from occurring.  Apparently the problem is most prevalent when rebooting one of the OTHER computers.

---

### Post by ltolledo on 2006-08-06
"scroll lock (2x) + m" worked for me. Am using surecom 2 port KVM switch. Now I can view both my U5.1 and WXP PCs alternately without the weird mouse movements on U5.1

---

### Post by em3raldxiii on 2006-08-07
Check this thread ... has a few fixes.

[http://ubuntuforums.org/showthread.php?t=187018&highlight=KVM](http://ubuntuforums.org/showthread.php?t=187018&highlight=KVM)

---

