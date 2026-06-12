---
title: "White screen after installing Beryl"
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by miLl3niUm on 2007-04-30
I had Ubuntu Feisty and a 1280x1024 screen resolution. I installed Beryl with [these]("http://ubuntuforums.org/showthread.php?t=428278") instructions and it was working fine. I formatted my PC (with Ubuntu again) and I couldn't see 1280x1024 in the options. Anyway, I solved this problem but when I install Beryl with the same instructions, when the logon screen loads:
[LIST=1]
[*]I type username (and hit enter)
[*]I type password (and hit enter)
[*]I see that small box in the middle of the screen (loading...)
[*]I see the desktop and then all the screen goes white. I can only see the mouse.
[/LIST]

NOTE#1: As I said before, Beryl was working fine before I format my PC.
NOTE#2: I think me video card is ATI.

Why do I have this problem?
Thanks :)

---

### Post by miLl3niUm on 2007-04-30
Bump

---

### Post by antiram on 2007-04-30
is this your (hardware) problem?
[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684)

at first use metacity and make glxgears working with hardware 3D.

---

### Post by miLl3niUm on 2007-04-30
> **antiram said:**
> is this your (hardware) problem?
[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684)

at first use metacity and make glxgears working with hardware 3D.

I will check it now but note that it was working fine before format.

---

### Post by esteth on 2007-04-30
this is a known problem. as a simple solution, open synaptic, or apt-get at the terminal, and force beryl's version to an older version. i beleive you use 0.9~beryl1, or something similar to that.

after reloading X and restarting beryl, all should be well.

---

