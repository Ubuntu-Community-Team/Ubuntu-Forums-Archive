---
title: "cannot boot after compile-fail"
date: 2009-06-20
forum: General Help
---

### Post by PampkenPai on 2009-06-20
... after I fail at compiling GIMP from source, because it was having troubles..

the thing is, before i could make install it, my keyboard locked up (like it does every few hours) and i couldn't type anything at all. all the menus refused to open, so on-screen keyboard wasn't an option.

since it already finished make, i just decided to restart .. on the first try, it did a routine check of drives (coincidence?) and then the splash screen with the loader bar came up and loaded. after that, it comes out to a black screen with just the "loading" cursor, which is movable... but it just stays at that screen forever.

i can use the live CD and boot from that, but i have no idea what to do then. 

i'm using ubuntu 9.04.

is there any way to fix this without having to reinstall ubuntu? if not, is there a way to back up all my info from the live CD? 

also, if anyone knows why my keyboard and menus would lock up at random intervals, i would appreciate that too.

thanks, 
dave.

btw: please direct me to the appropriate forum if this is not where to put it (:

---

### Post by nereid on 2009-06-21
What do the log files say in the /var/log folder? Start with a Live CD and mount your local hard drives.

To back up your files, just save the files in your home folder. Zip them up and put them on a USB stick or something like that.

Uhm, I can't help you about the lock up problems. But most of the time the log files should help you there too.

I hope that I could point you in the right direction.

---

### Post by PampkenPai on 2009-06-21
thanks for the reply.

i tried looking through the logs, but i'm not sure what exactly i'm looking for. i didn't see any error's in syslog, the gdm logs, or the xorg logs.. which were the only ones that i thought of.

however, i do see..

Jun 21 10:18:20 Desktop gdm[2876]: WARNING: Couldn't authenticate user 
Jun 21 10:18:42 Desktop last message repeated 11 times
Jun 21 10:18:44 Desktop console-kit-daemon[2711]: WARNING: Couldn't read /proc/2709/environ: Failed to open file '/proc/2709/environ': No such file or directory 
Jun 21 10:18:45 Desktop gdm[2876]: WARNING: Couldn't authenticate user 

in syslog.

i did a bit of googling and found that i could boot into my desktop without the Live CD by ctrl+alt+f1 on the black screen of fail and "sudo /init.d/gdm stop" followed by "startx /usr/bin/gnome-session"

it then boots into a fully functional desktop. it's as if nothing happened.

however, when i reboot, it still gives me that black screen w/ cursor. i can cope with having to ctrl+alt+f1 for a few days.. but that'll drive me mad.

---

### Post by PampkenPai on 2009-06-21
Update: I tried reinstalling xorg and gdm via Synaptic, and I tried to start gdm.. with "gdm" into a terminal.

It returns..

```
gdm[9157]: WARNING: GDM file gdm-daemon-config.c: line 2042 (): Cannot run seteuid to 0: Operation not permitted
GDM file gdm-daemon-config.c: line 2042 (): Cannot run seteuid to 0: Operation not permitted

```

---

### Post by nereid on 2009-06-21
Warnings don't mess up the X server, usually ;)

But you have narrowed down the problem to X.

gdm runs as a daemon and is started via the boot up scripts, so starting it via the commandline without going through the scripts won't work that well.

But the graphics worked fine before the incident with the Gimp?

What does ~/.xsession-errors say?

---

