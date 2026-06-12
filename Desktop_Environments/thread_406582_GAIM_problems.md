---
title: "GAIM problems"
date: 2007-04-11
forum: Desktop Environments
---

### Post by akuterrer on 2007-04-11
Hi all,

I just installed Ubuntu 6.06 and it works fine on my P3 laptop, however, my GAIM which comes together whem installing Ubuntu keeps crashing. Whenever I logon to GAIM for my MSN acct, it shows the buddy list and after a few seconds, it just closes. No error messages or whatever.

Any way tht I can uninstall and reinstall Gaim?
Any help or advise is very much appreciated!

---

### Post by Obor on 2007-04-11
Open gaim from terminal to see the error messages (Applications - accessories - terminal and type gaim)

If you want to reinstall gaim
system menu - administration - synaptic package manager - search for gaim - right click - mark for reinstall - apply

If reinstalling doesn't solve your problem and you only want to connect to msn - install  amsn

Either mark it for install in synaptic or paste into terminal
```
sudo aptitude install amsn
```

---

### Post by akuterrer on 2007-04-11
Hi Obor,

Thanks for the tips.

Here's the error message that is shown in Terminal :-

Gaim has segfaulted and attempted to dump a core file.
This is a bug in the software and has happened through
no fault of your own.

It is possible that this bug is already fixed in CVS.
If you can reproduce the crash, please notify the gaim
maintainers by reporting a bug at
[http://gaim.sourceforge.net/bug.php](http://gaim.sourceforge.net/bug.php)

Please make sure to specify what you were doing at the time,
and post the backtrace from the core file. If you do not know
how to get the backtrace, please get instructions at
[http://gaim.sourceforge.net/gdb.php](http://gaim.sourceforge.net/gdb.php). If you need further
assistance, please IM either SeanEgn or LSchiere and
they can help you.
Aborted

What should I do? Reinstall GAIM?

---

