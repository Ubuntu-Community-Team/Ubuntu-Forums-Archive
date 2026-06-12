---
title: "Gnome takes 15+ minutes to load with no network connection"
date: 2006-11-16
forum: Desktop Environments
---

### Post by NiksaVel on 2006-11-16
Hey all,

I've posted this question b4 but got no answers so I will try again:

I have a fresh ubuntu edgy install on my laptop.
Everything works great, gnome, kde and gnome+beryl (xgl) - it's all very good.

The only problem I have is when I try to run the laptop with no network connection - what happens is that I get to the logon screen normally, but after entering login/password gnome take 15+ minutes to load completely and than works okay. As soon as I configure a network connection or plug it in  - it resumes logging in in less than 10 secs...

Trying to switch session to KDE completely removes this problem...  so it's something gnome related. Using beryl or not has no effect...  this problem was present long b4 I first intalled beryl.


I don't have any extre programs autorstarting that might cause this.

If I disable all network adapters (wired/eth0 and wireless/eth1) the problem goes away.


When I try to login to failsafe gnome session, the problem remains, and I also get an error msg:

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

GNOME will still try to restart the Settings Daemon next time you log in.

this error does not appear on regular gnome session.



somebody please help me - this is quite a handicap since I have to login to kde, disable all network cards, logout, and than finally login to gnome to be able to work whenever I am not connected to the net.!!!  ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by alec on 2006-11-16
Saw this thread a day ago don't know if it will help.

[http://ubuntuforums.org/showthread.php?t=296625](http://ubuntuforums.org/showthread.php?t=296625)

But it seems to be a similar/related problem. Last in the thread gives a solution.

---

### Post by NiksaVel on 2006-11-17
PRAISE THE LORD!!!   This finally solved my probs!!!   Thanks a bunch man!

---

