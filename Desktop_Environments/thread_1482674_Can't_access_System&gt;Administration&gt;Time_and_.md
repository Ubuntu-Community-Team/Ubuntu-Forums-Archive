---
title: "Can't access System&gt;Administration&gt;Time and Date"
date: 2010-05-13
forum: Desktop Environments
---

### Post by pbwest on 2010-05-13
Lucid 10.04, auto upgraded from 9.10, accessed through NoMachine NX from my MacBook Pro 10.6 system.

When I try to access the time settings through the System > Administration > Time and Date menu, all I get is the greyed-out display with the message Not authotized to make changes at the bottom.

With other administration functions, I am asked for sudo-style authorization with my password. That doesn't happen with Time and Date.

Why is is so? What can I do about it?

---

### Post by quixote on 2010-05-15
I'm not familiar with NoMachineNX.  When you're trying to change time & date, are you in ubuntu, or in a Mac frontend of some kind?  If the latter, that's probably why.  System time is a very critical thing, and only plain old root (ie sudo) can change it.  Sudo coming in from a MacOS would look suspicious to linux, even if some sudo-type functions are allowed.

The way the menu you're talking about should look is it should be grayed out, but have a "click to make changes" button at the bottom.

The command line way to do this is using hwclock.  Type "man hwclock" (without quotes) in a terminal (Applications > Accessories > Terminal) for info on how to use the command.  If the problem is that the menuing interface has somehow lost the right permissions, the command line method will still work.

---

### Post by pbwest on 2010-05-15
NX is an ssh-based VNC-style remote interface. It's great.

When I'm attempting to access the time settings, I'm running a remote window on Ubuntu. See attached screenshot.

---

