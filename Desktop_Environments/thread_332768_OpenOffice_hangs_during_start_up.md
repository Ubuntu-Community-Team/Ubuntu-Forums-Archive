---
title: "OpenOffice hangs during start up"
date: 2007-01-06
forum: Desktop Environments
---

### Post by antipattern on 2007-01-06
I have a small problem with my OOo installation. Everytime I want to open any of the OOo Applications, the app gets stuck and shows the Splash Screen. 

Apart from that the terminal doesn't show any error output at all. 

So I tried "strace soffice", as someone in anoter forum (heise Online) suggested, which outputs this:

--- SIGCHLD (Child exited) @ 0 (0) ---
read(3, "", 128) = 0
close(3) = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 19378
clone(child_stack=0,
flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD,
child_tidptr=0xb7e3b6f8) = 19379
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 19379
--- SIGCHLD (Child exited) @ 0 (0) ---
clone(child_stack=0,
flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD,
child_tidptr=0xb7e3b6f8) = 19382
rt_sigaction(SIGTERM, {0x8054c2e, ~[RTMIN RT_1], 0}, NULL, 8) = 0
wait4(-1, 0xbfa15100, 0, NULL) = ? ERESTARTSYS (To be
restarted)
--- SIGWINCH (Window changed) @ 0 (0) ---
wait4(-1, 

Strangely this doesn't happen when I start OOo as root (gksudo).

For those who can't acces their crystal ball right now, my system details:
Ubuntu 6.10
latest OpenOffice 2.04

Anybody any suggestion about what to do?

Thanks in advance...

Regards, chrx

---

### Post by Hagar Delest on 2007-01-07
It may be a problem with the rights on the user profile directory.

Try to rename the hidden folder /home/<your user name>/.openoffice.org2, OOo will create a new one, this time it should have enough rights (don't run it as root of course).

For information, latest OOo version is 2.1, youcan install it from the RPMs, there are some threads about it.

---

