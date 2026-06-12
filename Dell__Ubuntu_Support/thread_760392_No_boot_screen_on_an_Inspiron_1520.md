---
title: "No boot screen on an Inspiron 1520"
date: 2008-04-20
forum: Dell  Ubuntu Support
---

### Post by sayakb on 2008-04-20
Hello all
I installed Ubuntu Gutsy amd64 on a Dell Inspiron 1520 of a friend of mine. I noticed that the boot screen used to come (boot screen: The Ubuntu logo with the orange progress bar) with the 32-bit Gutsy but it isn't coming with the 64-bit version. I tried changing the resolution in the usplash.conf file to 1280x800 but it still didn't work. The screen gets switched off at the time of the splash screen. What should I do to make it working. 
PS: No other problems on the laptop (everything resolved!!) but this minor glitch is a hindrance to perfection!

---

### Post by ridgeland on 2008-04-20
I want to follow this post because I have a similar issue.

I installed 7.10 on a Gateway PC that now uses a Dell monitor.  At first the install was a challenge with the monitor only saying something like "Cannot Display This Video Mode".  I got it installed OK by tweaking xorg.conf.  But now that it is installed during the boot and shutdown where I expect the splash screen with the orange progress bar I get "Cannot Display This Video Mode¨.  Is there something like xorg.conf that is being used outside the X-windows system?  I would expect the progress bar screens are not using X.

---

### Post by jespdj on 2008-04-21
Does your laptop have an nVidia 8xxx video card?

There's an old bug which is specific to the 64-bit version of Ubuntu and nVidia 8xxx cards - the boot splash screen doesn't show.

I'm now using 64-bit Ubuntu 8.04 RC on my M1530 (with nVidia 8600M GT) and the boot splash screen works now - it looks like this bug has finally been solved.

Try using 64-bit Hardy RC or wait a few days for the final release (it's due this Thursday, 24 April).

---

### Post by TehDuke on 2008-04-22
I also have a inspiron 1520 and i have the exact same problem. Just after loading the linux kernel, the screen turns off.

---

