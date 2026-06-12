---
title: "The connection speed is very slow in remote desktop, why ????"
date: 2010-09-23
forum: Desktop Environments
---

### Post by q8.legend on 2010-09-23
Hi

Why when you use remote desktop its sooooo slow. even when you use it over local network. Its kind a wired things !!!

I'm kind a new to ubuntu. in windows the connection was just great & i didn't suffer from it ever, like what did faced me in ubuntu...

I hope there is solution for that... Thanks alot ;)

Note:
I was using the remote desktop feature that is built in in ubuntu 10.04. and i tried to connect to it from windows using tight vnc and vnc viewer . All gave me the same result a slow connection :(

---

### Post by coilwinder on 2010-11-22
A possible solution / workaround:

Open terminal, issue the command:

gconf-editor

Then navigate to: desktop / gnome / remote_access. Enable the "disable_xdamage" setting.


I found the solution here: [http://start.ubuntuforums.org/showthread.php?p=9659063](http://start.ubuntuforums.org/showthread.php?p=9659063)

---

