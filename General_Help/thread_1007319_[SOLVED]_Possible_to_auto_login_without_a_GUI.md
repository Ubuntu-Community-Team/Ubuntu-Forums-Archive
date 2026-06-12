---
title: "[SOLVED] Possible to auto login without a GUI?"
date: 2008-12-10
forum: General Help
---

### Post by tra4d on 2008-12-10
Is is possible to have no login (or automatically login a particular user) without a GUI?

I have seen lots of posts with GUI programs handling the automatic login, but can't find any dealing with a command line system.  Is it possible?

I saw these two posts but they need to install other software.  The first one looks good, but can rungetty be installed without a GUI?

[http://ubuntuforums.org/showthread.php?t=727947&highlight=command+line+system+automatic+login](http://ubuntuforums.org/showthread.php?t=727947&highlight=command+line+system+automatic+login)

And this one is close, but it deals with a system that has a GUI, but doesn't want to use it to login:

[http://ubuntuforums.org/showthread.php?t=890517&highlight=command+line+system+automatic+login](http://ubuntuforums.org/showthread.php?t=890517&highlight=command+line+system+automatic+login)

Any help would be appreciated.

Regards,
Scott

---

### Post by sisco311 on 2008-12-10
if you have a working internet connection you can installl rungetty:

```
sudo aptitude install rungetty
```



edit the tty1 file:

```
sudo nano /etc/event.d/tty1
```
(Ctrl+x, y, Enter - save the file and exit)

and change:

> respawn
exec /sbin/getty 38400 tty1

to

> respawn
exec /sbin/rungetty tty1 --autologin **username**


replace **username** with your login name.

---

### Post by tra4d on 2008-12-10
So rungetty does not need a GUI?

---

### Post by tra4d on 2008-12-10
Now the system hangs at:

  * Running local boot scripts (/etc/rc.local)      [OK]

Any ideas?  (I can use tty2 and tty3, etc by using Ctrl + Alt + 2, 3, ... but tty1 seems to not work)

---

### Post by tra4d on 2008-12-10
Nevermind.  Had a typo.  Works great!  Thanks sisco311.

---

### Post by lardandweed on 2008-12-15
Cool! I was looking for a solution to this too.

So it's not possible to do this without installing extra apps?

---

### Post by tra4d on 2008-12-16
I think you need the extra app. if you don't have the GUI installed.

---

### Post by lardandweed on 2008-12-16
ah ic. kk. no biggie really.

thx!

---

