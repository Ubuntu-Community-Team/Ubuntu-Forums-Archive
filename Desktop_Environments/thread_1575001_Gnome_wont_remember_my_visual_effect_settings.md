---
title: "Gnome wont remember my visual effect settings"
date: 2010-09-15
forum: Desktop Environments
---

### Post by venturax on 2010-09-15
After i upgraded to 10.04, I experienced some problems, especially that whenever i log in my visual effects are set to None. If i select Extra its all good. But after log out / reboot etc., its set back to None.

Any idea, why this behaviour occurs?

I suspect some permission problems, but haven't been able to locate any as of yet.

---

### Post by twills805 on 2010-09-26
Hi, 

I have exactly the same problem after booting up this morning.

Restart and Visual Effects are set back to none in Appearance settings. I can change these to Extra which is what I have been running comfortably for months. It searches for available drivers, activates and runs fine for the entire session

On reboot it is all set back to none again...

Any ideas?

Thanks!

Tom


EDIT: to OP, just found this, it has a few solutions in it, let me know if any work- [http://ubuntuforums.org/showthread.php?t=1466162&page=2](http://ubuntuforums.org/showthread.php?t=1466162&page=2)

---

### Post by twills805 on 2010-09-26
Adding **/usr/bin/compiz --replace** to startup apps worked for me, there is a bug filed at [https://bugs.launchpad.net/ubuntu/+s...iz/+bug/572617]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/572617")

---

### Post by jim_deadlock on 2010-09-26
I happened to subscribe to this thread when I was experiencing the same problem a couple of weeks ago. I managed to fix it myself in the end, see if this works for you:

[http://ubuntuforums.org/showthread.php?t=1573846](http://ubuntuforums.org/showthread.php?t=1573846)

---

### Post by venturax on 2010-09-27
Just some information:

calling "compiz --replace" gave me this:
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!

Also as jim_deadlock suggests, locating metacity.desktop file failed, as i don't have one, where Hidden is set to true.

:sad:

Status is: I still have the problem. A colleague of mine installed 10.04 and it runs without problems. I'm the only one in the office, who has problems. But I'm also the only one, who have upgraded from 9.10. All the others are using a clean install. I don't wanna go that way. Then its better to live with the errors :cry:

---

