---
title: "Memory Leak (2GB RAM at 95% with Pidgin)"
date: 2008-06-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by keryonic on 2008-06-30
My Vostro 1310 crashes at least once a week. It is a memory leak and my system begins to be very slow. After a lot of patience, I succeed to launch "System Monitor" and I see that my 2GB RAM tops at 95% and CPU at 85%. The faulty program is Pidgin but I can't shut it down because it says "uninteruptible" (or something like that). The strange thing is that I had the exactly same problem with aMSN and Emesene (that is why I changed to Pidgin).

Question:

1. Anyone has got this problem?
2...and found a solution?
3. How to start "system Monitor" with shortcut (Ctrl-Alt-Del in Windows)?
4. How to kill an "uninteruptible" process?

I like Ubuntu but I am not sure it is ready to compete with Windows XP. It is sometimes too complicated, driver don't always exist and I don't find it more stable. But I like the Philosophy and the safety feeling (no virus) and I like to pursue the experience and I hope that soon I will be able to delete that Windows partition.

Thanks for your help.

---

### Post by damis648 on 2008-06-30
> **keryonic said:**
> 4. How to kill an "uninteruptible" process?

In terminal,
```
killall pidgin
```
or right click it and select "kill".

PS. Hope you can use Ubuntu full time and delete that windows partition. I am free of windows as of last week, and love it!

---

### Post by vandorjw on 2008-07-26
I have the same problem, but has only started recently.
Is there no better method than simply killing the program?

I open the system monitor, and ended pidgin.
At first it said "un-interruptible" like the first guy said, but then about 10 seconds later, pidgin closed.

This problem only occurs when I run Cnc Renegade in Wine (version 1.1.1)
Today I will update Wine to 1.1.2 and hope that it fixes the problem.

---

### Post by Kzin on 2008-07-29
> 1. Anyone has got this problem?
I do.
> 2...and found a solution?
Not yet, anyone?  See below for further details.
> 3. How to start "system Monitor" with shortcut (Ctrl-Alt-Del in Windows)?
I would check System>Preferences>Keyboard Shortcuts, seems like a good place to start.
> 4. How to kill an "uninteruptible" process?
I tried killall pidgin
I tried kill -9 <processID>
I tried Right Click>Kill, Stop and End process.
I tried setting priority low/high and killing.

I find that you can actually open another instance of Pidgin.

Actually, as it turns out, you cannot kill processes in the D state (I found pidgin's state using ps ax).  If anyone can I'd like to know how exactly.  Apparently it means the process is on some critical path or magical dragonquest for the kernel... or something.

I'm gunna reboot now.  The most recommended step for eliminating these buggaz.  Think I'm going back to aMSN.

> I like Ubuntu but I am not sure it is ready to compete with Windows XP
Ya, it can get annoying... XP can too... I'm never deleting my XP tho... I use it to play BF2142, other games too...  My Neverwinter Nights plays in Linux, but its not enough.
I also use Protools, if I can get my DIGI001 working in Linux like a dream, that'd be awesome.

Point is, yea, each one has its use.  I use UBUNTU 90% of the time and Windows only when I want to use the DIGI or play video games.  "Wintendos".

References;
[http://www.linuxforums.org/forum/redhat-fedora-linux-help/50073-can-anybody-help-out-kill-process-status-d-iam-not-able-start-application-because.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/50073-can-anybody-help-out-kill-process-status-d-iam-not-able-start-application-because.html)
[http://linuxgazette.net/issue83/tag/6.html](http://linuxgazette.net/issue83/tag/6.html)
[http://www.thinlincusergroup.se/forum/teknik/373040919](http://www.thinlincusergroup.se/forum/teknik/373040919)

---

### Post by airydragon on 2009-11-08
got same problem. even i logout pidgin process still exist. good news is i can kill it instantly on console after logging out.

PS: on kubuntu karmic

---

