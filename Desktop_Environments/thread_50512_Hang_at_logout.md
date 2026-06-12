---
title: "Hang at logout"
date: 2005-07-20
forum: Desktop Environments
---

### Post by Garrett on 2005-07-20
I couldn't locate a thread on this (yet) so here is my problem.

GNOME rules and runs flawlessly BUT when I hit System> Log Out, GNOME just freezes up. I can still move my mouse and I can ctrl+alt+backspace out of the xserver and reboot or logout there, but that is silly. Any idea what might be causing this?

Also, just on a sidenote, I never was able to guess the command to boot down without rebooting.... I tried shutdown but it wanted me to input extra parameter. Is there a simply command?

Thanks!

 ](*,)

---

### Post by Lord Illidan on 2005-07-20
What was the extra parameter?

Anyway try sudo halt

---

### Post by Saru san on 2005-07-20
For sidenote. Almost every command has a 'man' entry...```
$man shutdown
```...will tell you everything and more than you need. For further reading try...```
$man man
```What it needs is for you to be mean to it with...```
$sudo shutdown now
```Not sure if you can put 'damnit' at the end but it's worth a try. ;)

---

### Post by Garrett on 2005-07-20
Thanks at least I know I can shut down the old fashioned way... I'd much rather that my x didn't freeze upon log out though!  :| 
Any ideas?

---

### Post by muriloq on 2006-10-31
> **Garrett said:**
> I couldn't locate a thread on this (yet) so here is my problem.

GNOME rules and runs flawlessly BUT when I hit System> Log Out, GNOME just freezes up. I can still move my mouse and I can ctrl+alt+backspace out of the xserver and reboot or logout there, but that is silly. Any idea what might be causing this?

 ](*,)

Same problem here - I'm using Xubuntu (6.10 Edgy Eft). It hangs when logging out Gnome and XFCE sessions. And Ctrl+Alt+Backspace (or opening another term with Ctrl+Alt+F1, for example) doesn't help in my case, I have to turn off power and restart the system. 

Pressing Ctrl+Alt+Backspace also hangs exactly like when I choose the Log Out option. It's extremely annoying... :-(

---

### Post by Simon G Best on 2006-12-13
> **muriloq said:**
> Same problem here - I'm using Xubuntu (6.10 Edgy Eft). It hangs when logging out Gnome and XFCE sessions. And Ctrl+Alt+Backspace (or opening another term with Ctrl+Alt+F1, for example) doesn't help in my case, I have to turn off power and restart the system. 

Pressing Ctrl+Alt+Backspace also hangs exactly like when I choose the Log Out option. It's extremely annoying... :-(

Sounds exactly like my problem!  (Although I haven't tried the Ctrl-Alt-Backspace thing, yet.)

---

### Post by raul_ on 2006-12-13
- bump -

---

### Post by cwhitt on 2007-01-11
There seem to be a few different types of problems with logout and/or shutdown.  If you have an Intel chipset with onboard video, the problem may be caused by kernel panics when the X server is being shut down.  Don't know about a fix, but a good workaround was posted here:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34697](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34697)

You need to change a setting in your BIOS Advanced -> CPU Configuration -> Execute Disable Function to ENABLED.  Somehow this prevents the shutdown of the X server from causing a kernel panic.

Cheers

---

