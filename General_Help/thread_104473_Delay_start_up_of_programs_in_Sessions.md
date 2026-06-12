---
title: "Delay start up of programs in Sessions"
date: 2005-12-16
forum: General Help
---

### Post by kwaanens on 2005-12-16
In brief:
Want to have network-manager, gmail-notify and firestarter start up on login.
Problem is, nm-applet doesn't hook up to my wlan fast enough, so I get errors from FS and Gmail-notify.
Have set nm-applet to 10 now, and would additionally like to delay the start of the other two.
```
sleep 10 && sudo firestarter
```
works from terminal and by ALT+F2, but not from System > Preferences > Sessions. How do I do that?

---

### Post by Mguel on 2005-12-17
I need the same thing...

The tray icons of programs don't show on the tray, but on the desktop...

---

### Post by Mguel on 2005-12-17
I managed to make it work by creating a text file with the following:
```
#/bin/bash
sleep 9 && amule
```
And pointed to that on System | Preferences | Sessions -> Startup Programs

I'm not sure if this is a bad/mad way to do it, since I'm pretty new to linux, but it works... ;)

---

### Post by zoiks on 2005-12-17
[QUOTE=Mguel]I managed to make it work by creating a text file with the following:
```
#/bin/bash
sleep 9 && amule
```
And pointed to that on System | Preferences | Sessions -> Startup Programs

I'm not sure if this is a bad/mad way to do it, since I'm pretty new to linux, but it works... ;)[/QUOTE]

IMHO it's perfectly fine to do it this way.  In fact, perhaps in the sessions editor you can add a & at the end of the command to have it run in the background immediately.  That way it doesn't delay the other session startup commands.

---

### Post by Mguel on 2005-12-17
[QUOTE=zoiks]IMHO it's perfectly fine to do it this way.  In fact, perhaps in the sessions editor you can add a & at the end of the command to have it run in the background immediately.  That way it doesn't delay the other session startup commands.[/QUOTE]
Thanks!

I didn't consiedered it could delay the other tasks, so thanks for the tip. Do you mean to have something like this on the session start program:
```
/home/user/scripts/amule-sleep &
```

Cheers,
Mguel

---

### Post by zoiks on 2005-12-18
Exactly.  I haven't tried it, though, just so you know.  But it should background the program that starts up amule with a delay, so that way the other sessions commands can run right away while this one delays and does its thing.

---

