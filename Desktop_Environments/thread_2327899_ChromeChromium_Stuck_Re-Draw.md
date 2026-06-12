---
title: "Chrome/Chromium Stuck Re-Draw"
date: 2016-06-15
forum: Desktop Environments
---

### Post by clalian on 2016-06-15
Hello everyone,
I am running a fresh 16.04 install of Xubuntu.
I installed Google Chrome, and later also tried Chromium.

The problem is that after the screen saver gets activated on my laptop, I unlock the screen: 
Yet now Chrome (or Chromium) is "stuck": it does not "re-draw" its contents.

I can Ctrl+T and open a new tab, yet that new tab is not shown on-screen.
I have to switch workspaces back and forth, and when I come back Chrome has re-drawn that new tab.

This is driving me insane.
If it happened once per day, it would be an annoyance... yet as it stands right now, it's constant.
I cannot let my laptop lock my screen.

I found this bug report: [https://bugs.chromium.org/p/chromium/issues/detail?id=355720](https://bugs.chromium.org/p/chromium/issues/detail?id=355720)

Any suggestions what I can do?
I am almost at the verge of switching out of Xubuntu (XFCE) just because of this bug.

All help is appreciated!

---

### Post by clalian on 2016-06-16
Hello everyone,
I changed the video driver, and still having the same problem.

I went into Settings --> Additional Drivers
And selected: Using Processor microcode firmware for Intel CPUs from intel-microcode (proprietary)

I then rebooted... yet still running into the same problem.

Any idea what I could do?

---

### Post by roger_1960 on 2016-06-19
Hi

If you going into chrome's settings - advanced, and disable "use hardware acceleration where available" does that help?

---

### Post by RobGoss on 2016-06-19
Hello and welcome, This may be a silly question but have you try uninstalling Chrome and reinstalling it again?

---

### Post by clalian on 2016-06-20
> **roger_1960 said:**
> Hi

If you going into chrome's settings - advanced, and disable "use hardware acceleration where available" does that help?

Hello!
I just dis-abled the "hardware acceleration"... going to test it out, and report back on how it works.
Thank you!


> **RobGoss said:**
> Hello and welcome, This may be a silly question but have you try uninstalling Chrome and reinstalling it again?

Hello Rob!
As soon as I finish the "testing" of Roger's suggestion above, I will try uninstalling and re-installing.
It can't hurt!

---

### Post by clalian on 2016-06-21
I wanted to update:
Up until now, Google Chrome has worked correctly with the "re-draw" issue.
I will update later (in about a week) to re-confirm if it's working fine!

---

