---
title: "VNC Server at computer startup"
date: 2006-01-23
forum: Desktop Environments
---

### Post by geekphreak on 2006-01-23
I think this was asked before, but I'll ask again, in case there has been a success on this issue:
how to set up vnc server so it starts up when the computer starts, not after someone logs in? I'd like to be able to login/logout/restart remotely. I looked at some scripts in rcX.d directories, but could not figure what exactly the prefix in front of the service name meant. 
Did anyone succeed getting vnc server to load at computer boot time under Ubuntu? What would a script in rcX.d directory to accomplish this look like? I tried just putting vncserver or Xvnc or vino but it did not work. Any help would be greatly appreciated.

---

### Post by soulestream on 2006-01-24
im not at my ubuntu machine currently, but if its like any other distro you should be able to put the command you use to start it in /etc/rc.local

also if you are using gnome you can just enable the gnome remote desktop under "preferences" I think. That is always running.

soule

---

### Post by cwaldbieser on 2006-01-24
[QUOTE=geekphreak]I think this was asked before, but I'll ask again, in case there has been a success on this issue:
how to set up vnc server so it starts up when the computer starts, not after someone logs in? I'd like to be able to login/logout/restart remotely. I looked at some scripts in rcX.d directories, but could not figure what exactly the prefix in front of the service name meant. 
Did anyone succeed getting vnc server to load at computer boot time under Ubuntu? What would a script in rcX.d directory to accomplish this look like? I tried just putting vncserver or Xvnc or vino but it did not work. Any help would be greatly appreciated.[/QUOTE]
You could have the "init" super-server daemon to run it.  See "man inittab".  You could alternatively add it to the SysV directories with the "update-rc.d" command (see man update-rc.d).  The script really just needs to execute the vncserver program in the background.

I think an advantage to using init would be that if the server gets killed accidently, init will try to restart it, and if it keeps dying, it will stop trying to restart it and try again later.  It will also log problems in the system log.

I find all sorts of nifty tricks like that in O'Reilly's "Linux Server Hacks" and "Linux Server Hacks 2".

---

### Post by geekphreak on 2006-01-24
[QUOTE=soulestream]im not at my ubuntu machine currently, but if its like any other distro you should be able to put the command you use to start it in /etc/rc.local

also if you are using gnome you can just enable the gnome remote desktop under "preferences" I think. That is always running.

soule[/QUOTE]
rc.local does not exist, I tried it.
Gnome remote desktop is enabled when a user logs in, I would like it to start when the computer starts. 
I will try inittab hacks and report later.

---

### Post by Tichondrius on 2006-01-24
[http://www.ubuntuforums.org/showthread.php?t=42941](http://www.ubuntuforums.org/showthread.php?t=42941)

---

