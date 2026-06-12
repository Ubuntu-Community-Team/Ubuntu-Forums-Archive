---
title: "Non KDE programs are multiplying!"
date: 2005-07-08
forum: Desktop Environments
---

### Post by SGC on 2005-07-08
When I run a non-KDE program, it starts many instances of the same program; java-based programs starts 60 instances of java, beep-media-player and python starts 3 instances,  gimp and aMule starts 2 instances, and so on for the rest of the programms

When I say instances I don’t means there are two or three windows of the application, they are listed in the processes table (KDE System Guard)

What I couldn’t understand is how there are 60 instances of java; each one of them uses more than 65 mb of Ram and the system works normally without any slowdown

Could anybody helps me in solving this unusual problem

---

### Post by ltmon on 2005-07-08
Firstly, memory isn't as simple as all that.

The programs may be using shared libraries.  For example, if you see Gimp and Gaim each taking 50MB it is likely that libraries common to them both (e.g. gtk, gnome libs) are taking much of that.  Even though that memory is counted twice (once for Gimp and once for Gaim) it is really only taking up a single instance.  This is probably why everything looks memory hungry, but really isn't.

I hope I explained that well enough :)

The java one is interesting.  The "where'd all these java's come from" problem is an old one, where Java threading operations involved starting multiple instances.  In more recent kernels (i.e. since mid-2.4 series or something) there has been improvements to the NPTL (posix thread library) that stopped this occuring.

Maybe ksysguard is screwy.

Try typing

> ps aux | grep java | wc -l

into a console to find out how many java processes are on your system.  ALternately type

> top

to get a realtime monitor of the most system-hungry applications (initially it's sorted by cpu usage, but press 'M' to sort by memory use).

If this output is significantly different to ksysguard, then we know what the culprit is.

Cheers,

L.

---

### Post by SGC on 2005-07-08
Firstly, Thanks for your replay and the clearfication about the Ram 

[QUOTE=ltmon]
Try typing

> ps aux | grep java | wc -l

into a console to find out how many java processes are on your system.  ALternately type

> top

to get a realtime monitor of the most system-hungry applications (initially it's sorted by cpu usage, but press 'M' to sort by memory use).

If this output is significantly different to ksysguard, then we know what the culprit is.
[/QUOTE]

The first command returns 63, and top command output is similar to ksysguard.

I want to mention that this problem just started two days ago.

---

