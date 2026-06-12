---
title: "Dual Monitor - xorg.cnf messed up my system"
date: 2011-05-06
forum: Desktop Environments
---

### Post by mabooali on 2011-05-06
Hello, My name is Masood. I recently installed a 64-bit version of Ubuntu desktop on a machine that i had built for my CCIr practices:

system:

Intel i7 - 920 processor
6 Gig of RAm (three channel, etc crossfire- latest)
professional Enhanced grade MSi motherborad


AND finally a Redeon 6750 graphoc card - a hogh end Video card

two monitors, flat panel LCDs

so spent lits iof money to invest on my CCIE exam.

in setting up two monitors (using two digital I guess called DVI ports in the bac of the card) i attached two monitors afteri had the driver an dutilioties for that ATI Redoen card installed and Ll seened to had worked well expect both monitors were acting as one! no dragging of an application to the second monitor was available.


in the graphic utility control system, I tried to enable Xerocima (not sure about the spelling!) but it was grayed out!

after reaearching the web I came across thsi solution that asked to tweak the file under /etc/X11.xorg.cnf (i beleive that is eh file!/) and took a back up of the unchanged origial file. system asked for restart and I did - Now the problem:


it boots up to where I see the dots across the screen right before the login screen usually comes up but gets stuck there and nothing happens!

I tried to get a command prompt at boot uop and restor the original file but i couldn't.


I have spent a lots of time setting up this machine with the applications and utilities that i need to do my work like GNS3 and associated .net files, Cisco IOS, etc and just cannot afford to rebuild plus with Linux rebuilding shouldn't be an option. th esystem is too smart not to load an dingore tha simple changes of tha file ( a 1 was changed toa 0:confused:) i know that says alot but Linux is that smart to set to default if a single file is crruptted!?

I really need help in getting this resolved. any thoughts , feedback, possible resolutions from your guys is appreciated.

best Regards,

Masood

---

### Post by ajgreeny on 2011-05-06
Hold Shift after the power-on button and you will get the grub menu.  From there choose the second entry which should be "recovery mode" for the kernel that you use.  Now choose command line and when you get to the root prompt (root@<hostname>:~# use the command ```
mv /etc/X11/xorg.conf /etc/X11/xorg.confbak
```which will rename that file as xorg.confbak.

You can then use a similar command to restore the file that you already backed up by using ```
mv /etc/X11/xorg.*backup* /etc/X11/xorg.conf
```but use the name you gave your backup, of course.

Now reboot with the command ```
reboot
```and hopefully you will be back to where you were before you

---

