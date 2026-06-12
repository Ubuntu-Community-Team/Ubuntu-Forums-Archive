---
title: "OpenOffice hangs at splashscreen"
date: 2006-06-04
forum: Desktop Environments
---

### Post by SKK on 2006-06-04
Hi there!

Just installed Dapper as my primary OS and couldn't be happier for doing so but for one thing...

I can't get OpenOffice to start! Everytime I try from the menu, by doubleclicking on a document or from command line it simply just showes the splash and then does nothing. I even started it last night before i went to bed and let it run until this morning just in case it had some serious thinking to do, but still it's just the splash.

I've reinstalled it, I've removed everything and then reinstalled it and all I can think of right now is a complete reinstall of Ubuntu, but I thought I'd try on this great forum first!

When starting from command line there's no output - it just waits - but ps aux shows:

stekar@sheridan:~$ ps aux | grep office
stekar   24207  0.0  0.2   3404  1372 pts/0    S+   12:14   0:00 /usr/lib/openoffice/program/ooqstart
stekar   24209  0.0  0.3   4180  1676 pts/0    S+   12:14   0:00 /bin/sh /usr/lib/openoffice/program/soffice -splash-pipe=6
stekar   24220 85.0  6.6  95384 34256 pts/0    Rl+  12:14   0:22 /usr/lib/openoffice/program/soffice.bin -splash-pipe=6
stekar   24257  0.0  0.1   2740   788 pts/1    R+   12:14   0:00 grep office
stekar@sheridan:~$

Ideas what to do anyone?

---

### Post by SKK on 2006-06-04
No one?

Anyway... A little update... When I run strace ooffice it repeats...

write(4, "C\2\5\0\1\0\300\2\2\0\300\2\f\0\f\1\240\1\6\0F\0\5\0\1"..., 40) = 40
ioctl(4, FIONREAD, [0])                 = 0
poll([{fd=5, events=POLLIN|POLLPRI}], 1, 0) = 0
nanosleep({0, 20000000}, d=5, events=POLLIN|POLLPRI}], 1, 0) = 0

...over and over again until I terminate it.

Can anyone make heads or tails of this?

---

### Post by Dave Klinzman on 2006-06-21
I posted a problem a week or so after you posted this thread and got the same response - NOTHING!

My issue is exactly the same but I can add a couple of observations as well.  Doing a "top" command in a terminal window shows a program named "javaldx" looping and taking >90% CPU.  When it is killed, a program named "soffice.bin" jumps in and takes over at >90% CPU.  When that is killed, the everything comes back to normal.

Hopefully, by my adding to this thread, it will bump it back up in the forum and someone will have a suggestion for us.

---

