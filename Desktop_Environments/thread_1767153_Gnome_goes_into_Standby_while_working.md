---
title: "Gnome goes into Standby while working"
date: 2011-05-25
forum: Desktop Environments
---

### Post by Pay87 on 2011-05-25
Hey,
I just switched back to Ubuntu since I got my SSD and Ubuntu feels now very nice..

I just was confronted with one problem. At my Home PC I was working normally using FileZilla and drag and dropped something from FTP to local machine, then suddently my PC locked and the Screensaver appeard. I mean this Matrix Saver is nice but not when you want to work :)

Then first I thought it simply locked the workspace and tried to login, but it did not accept any key input, then it just went to standby after some sec..

I really wonder how that can happen, I had deactivated automatic standby in the energy settings, because I don't use it.

Now I deactivated the energy app in the startup settings maybe that helps too.. I hope this don't happens again, but anyway maybe some of you know what settings I might can check, or what could cause this issue?

Thanks!! :guitar:

---

### Post by Krytarik on 2011-05-25
There seem to be quite a number of issues/bugs with "gnome-screensaver" and/or "gnome-power-manager" of Natty currently, which I presume you are running.

To work around that until they get fixed, you could try "xscreensaver", see my earlier post regarding it:
[http://ubuntuforums.org/showthread.php?p=10385503#post10385503](http://ubuntuforums.org/showthread.php?p=10385503#post10385503)

Greetings.

---

### Post by Pay87 on 2011-05-26
Thanks for your answer I installed xscreensaver and removed the gnome one lets see if this issue happens again :)

Just one thing it seems like the xscreensaver deamon does not startup automatically, is there a easy fix for this? :P

---

### Post by Krytarik on 2011-05-26
> **Pay87 said:**
> 
Just one thing it seems like the xscreensaver deamon does not startup automatically, is there a easy fix for this?
Maybe by just adding it to "Startup Applications", as described in the thread I linked to, in the third level :P:
[http://ubuntuforums.org/showthread.php?t=1358946](http://ubuntuforums.org/showthread.php?t=1358946)

---

