---
title: "Gnome is slow to start and often hangs"
date: 2009-01-09
forum: Desktop Environments
---

### Post by Glenhawk on 2009-01-09
I am typing this via an XFCE session on my Pentium Dual core 1.8GHz with 4GB RAM and a 512MB Nvidia Graphics card.
I am running UBUNTU Hardy with Kernel Linux 2.6.24-23-generic and GNOME 2.22.3. I usually use the dual outputs of my NVidia card to run "Separate X Screens" on my two monitors but I have also tested with only one monitor active.

Under XFCE this PC responds very quickly as you would expect. Under GNOME it takes at least 5mins for the desktop to load and then whilst using it I will get several hangs of varying lengths. For example I try to open my documents folder and it hangs, I try to save a file from an email and it hangs, I click the shutdown button on the secondary X screen it hangs, etc.
Sometimes it will start up in GNOME (after a time) and state that an applet (fast user switching is one I recall) has failed and asks if I would like to delete it. The last time I got these messages I said YES to deleting them but still no improvement.

My best guess is that it is something to do with Nautilus or Compiz but I can't find any fixes when googling for "Slow boot nautilus hardy" or "nautilus gnome slow hardy" or other variants. I am trying to turn off compiz to see if that makes a difference but I have already reduced the screen effects with no result.

Does anyone have any ideas for me?

---

### Post by Glenhawk on 2009-01-11
I tried switching off Compiz and the only thing that changed was that I lost the upper and lower toolbars (system tray, menus, etc.).
I forgot to mention but it is the 64-bit version that I am having problems with. I have two other machines at work running hardy i386 with no problem (I'm using one of them now) and I have two PCs at home running Mythbuntu hardy (one i386 and the other amd64) with no problems. I even have a wubi install of hardy amd64 on my wifes laptop that only sees occasional use but also seems to have no problem.
Could it be a combination of NVidia drivers, Compiz and Gnome 64-bit?
Any ideas now?

---

### Post by lswb on 2009-01-11
A system with those specs should work very well with any DE. By comparison, my laptop is a 1.4Ghz Pentium M (single core) and boots to gdm login in about 25 seconds, then logging in to gnome takes maybe another 20 - 25 seconds.

The problem could be in a number of places. I would start by checking logfiles for any errors. /var/log/syslog and ~/.xsession-errors come to mind for starters. Sorry but I have no direct experience with 64 bit problems. (Until this past summer my main computer was a Pentium 3 650, which BTW also has a reasonable boot time with gnome/hardy)

---

### Post by Glenhawk on 2009-01-12
hmmm.... I just turned all the visual effects of the desktop off and it so far seems to be functioning flawlessly.
I thought I had turned Compiz off, maybe I hadn't.
The trials continue...

---

### Post by Glenhawk on 2009-01-16
I threw it in and installed intrepid instead. Now the only issue I am having is the launchers on the toolbar in the second x screen are causing errors. I'll call this thread ended and if I can't find a solution to the launcher errors I'll start another.

---

### Post by graysky on 2009-01-16
You guys are barking up the wrong tree - this is a known issue with Intrepid.

[http://ubuntuforums.org/showthread.php?t=1002049](http://ubuntuforums.org/showthread.php?t=1002049)

---

### Post by Glenhawk on 2009-01-17
Not really, my problem is directly related to Nvidia dual x screens and the compiz fusion effects. Since the last message I started getting the same problems than from Hardy.
Last time I tested switching off compiz effects I don't think I restarted. This time I switched them off, restarted and without them running it all seems to be working fine.

---

### Post by graysky on 2009-01-17
@Glenhawk - do this:

Reboot but don't log in.  Watch the clock on your gnome login screen.  After 2 min or so, go ahead and log in.  Now, post the time you logged it and the log files so we can help.

System>Administration>System Log will get you there.

Post your: auth.log, daemon.log, debug, kern.log, messages, syslog, user.log, and Xorg.0.log.

---

