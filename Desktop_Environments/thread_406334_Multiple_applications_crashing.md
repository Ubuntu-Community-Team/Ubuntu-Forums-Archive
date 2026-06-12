---
title: "Multiple applications crashing"
date: 2007-04-10
forum: Desktop Environments
---

### Post by pcharb on 2007-04-10
Good day,

I'm using Ubuntu 6.06. This is a pretty fresh install. I have multiple applications that randomly crash on me (ie. Firefox, thunderbird, rhythmbox, gnome-panel). They seem to die with 'Segmentation fault' but even that is not consistent. The behaviour is completely random. Sometimes it will run a whole evening with no crashes and other times I can't seem to get applications to work for more then a few minutes. A reboot sometimes helps.

I did an update just in case this was a resolved issue and it didn't solve the problem.

I have a feeling that it is a common component/process that is crashing. Maybe I'm wrong. How can I get a trace of what is happening? Any suggestions would be greatly appreciated.

Thank you in advance for your help,
LPC

---

### Post by pcharb on 2007-04-21
I found out that strace can trace trace system calls and signals. I don't know how helpful that is.

My crashes are still random. Last last one I got gave me the following strace:

read(3, 0xbf93233c, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(3, "\1\30[\260\0\1\0\0\0\0\0\0\240T\34\10\21N\31\10\0\0\0\0"..., 32) = 32
readv(3, [{"\377\377\377\0\377\377\377\0\377\377\377\0\377\377\377"..., 1024}, {"", 0}], 2) = 1024
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
unlink("/home/pierre/.mozilla/firefox/g0makt65.default/lock") = 0
rt_sigaction(SIGSEGV, {SIG_DFL}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [SEGV], NULL, 8) = 0
tgkill(6012, 6012, SIGSEGV)             = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++

Any idea what this means?

Thanks,
LPC

---

### Post by AngryKlown on 2007-04-21
If your crashes are "completely random," it's possible your memory or CPU are not getting enough voltage or are overheating, or your memory or CPU have gone bad. Do you overclock? Do you have adequate case cooling?

You can check the integrity of your memory with memtest, and the integrity of your CPU with prime95.

---

### Post by pcharb on 2007-04-26
To answer the post about hardware issues. I run a dual boot and have no problem with my windows install.

Often when applications crash I end up getting kicked back to the login screen. It's not always this way but more often then not. I found out some folks have this issue because of corrupt user settings. I created a new user and within a few minutes of login as this user applications where crashing.

Seems like this issue is boot dependent. If I'm having trouble I just reboot and then everything runs fine.

This link contains some interesting info about figuring out why firefox dies:
[https://wiki.ubuntu.com/MozillaTeam/Bugs](https://wiki.ubuntu.com/MozillaTeam/Bugs). Unfortunetly I haven't been able to log a crash yet.

LPC

---

### Post by Iron-Monk on 2007-05-01
I am having the same problem, it is completely random. It seems to be fixed on just a certain program, other programs run fine.  From time to time completely random programs that i haven't ran in a while or just installed will cause a  "Segmentation fault (core dumped)" error when i try to load them,  other programs run fine. After I log out and then Back in it seems to be fine, and also when the main user of the computer runs the programs they Run fine. Just hate to log out and back in all the time.

---

### Post by pcharb on 2007-05-01
Since I wasn't seeing too much action on this thread I decided to open a bug on launchpad. You can find it here: [https://bugs.launchpad.net/ubuntu/+bug/110687](https://bugs.launchpad.net/ubuntu/+bug/110687)

Hopefully this gets fixed!

LPC

---

