---
title: "Mouse problem - not being able to click anymore at random"
date: 2009-01-21
forum: General Help
---

### Post by Kyosys on 2009-01-21
Basically, the problem I'm having is that sometimes, I'm suddenly unable to left or right-click and scroll. I can still move my mouse, but I can't do anything with it. The keyboard still works fine. It's very frustrating because I can't seem to find a solution besides rebooting.

I run a M3N78 EMH HDMI with a hama wireless mouse.

Any help would be appreciated

edit: oh; I'm running ubuntu 8.10

---

### Post by Kyosys on 2009-01-29
c'mon people. This problem is annoying the hell out of me. Oh, and restarting X will also work to fix it.

---

### Post by Willberto on 2009-01-29
I have the exact same problem, posted here:
[http://ubuntuforums.org/showthread.php?t=1053554](http://ubuntuforums.org/showthread.php?t=1053554)

> About once every few hours my mouse buttons stop working. I can still move the cursor and use the keyboard however. This immediately happens sometimes when I do stuff like switch workspace, open up the mouse preferences or resize a window. It has done this since I first installed Ubuntu a few days ago. Anyone know how I might resolve this issue?

---

### Post by Kyosys on 2009-01-29
Maybe we should file a bug report? Seems like nobody knows the answer, and googling didn't help much either.

---

### Post by Willberto on 2009-01-29
Also my mouse is wireless as well.  The Logitech MX1000.

Also, how do I got aobut restarting x via command?

---

### Post by Kyosys on 2009-01-29
CTRL + ALT + BACKSPACE

it'll close all your graphical programs, though.

---

### Post by dcstar on 2009-01-29
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301)

[http://bugs.freedesktop.org/show_bug.cgi?id=18668#c9](http://bugs.freedesktop.org/show_bug.cgi?id=18668#c9)

I suffered from this with my 8.04 system after some upgrade last year, I have just done a fresh 8.04 install (with all upgrades) and it is ok so far.........

My theory it is some configuration change that was subsequently removed but the bad changes were never rolled back (so updating now doesn't cause the problem).

It is affecting many people over a long period of time (with many bug reports in many areas), so it is a really bad one that has proved impossible to track down so far.

---

