---
title: "How do I set options when recompiling ubuntu packages"
date: 2007-05-04
forum: Desktop Environments
---

### Post by snelo on 2007-05-04
I've looked at the Howto [http://ubuntuforums.org/showthread.php?t=101097](http://ubuntuforums.org/showthread.php?t=101097) on "HOWTO: Recompile packages for your system - Ubuntu Forums"  - But I'm not trying to recompile my package to optimise for my CPU - I want to recompile the squid package to retain control of it using apt and also allow the X-forwarded-for headers so I can have DansGuardian in front of squid but still set various access rules (based on which PC is accessing the Internet).  The howto describes using CFLAGS but that seems to set flags to gcc and then it doesn't work.

There are several files that seem to be interconnected - the configure configure.in Makefile and others and I really don't know which one I should change or should I do something else.

I have the source files down but... what next?

---

