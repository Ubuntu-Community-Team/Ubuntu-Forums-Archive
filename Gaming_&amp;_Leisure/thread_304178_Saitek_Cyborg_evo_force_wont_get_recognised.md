---
title: "Saitek Cyborg evo force wont get recognised"
date: 2006-11-21
forum: Gaming &amp; Leisure
---

### Post by mr.minister on 2006-11-21
Hi, i`ve just bought an "Saitek Cyborg evo force" joystick but it does not even get recognised. Here some info about my system

```
$ uname -a
Linux andreas 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

This is an up to date ubuntu edgy with kde installed. Upgraded by dist-upgrade from dapper.

```

I already tried google and this forum search.
Thanks in advance for any help :D

---

### Post by mr.minister on 2006-11-21
SOLVED!
Just restarted (second time) and now it works somewhow :) Just need to get the force feedback working and it the axes don't work in X2, only buttons

---

### Post by rengolin on 2007-05-16
Running jstest /dev/input/js0 it shows that the XY axis' values are random and there is a button 12 always pressed but there is no such button on this joystick.

What's happening? Seems like the joy module is reading the data wrong from USB...

---

### Post by rengolin on 2007-05-16
Found it, the data is coming perfectly from the joystick but the kernel module is making a mistake in the correction factor at drivers/input/joydev.c:523-533

If anyone is more familiar with the code, please investigate. Otherwise I'll take a look in the weekend.

---

### Post by rengolin on 2007-10-22
I've submitted the problem, Jiri Kosina (Suse) fixed and is up to enter the Kernel anytime now.

---

### Post by Sockerdrickan on 2007-10-22
That took some time lol

---

### Post by rengolin on 2007-10-22
It sure did! I've posted a few patches to auto calibrate the joystick but Jiri was sure he could find the source and fix it, and he did. At the end it was the non-LED output to the joystick that had to be ignored in HID or it'd scramble the axis ranges.

There is still one minor problem, the HID is initializing one more button that there it had detected, constantly pressed. This bug have some bad effects on some games (such as X-Plane) that accepts any button click as confirmation for dialogs... ;) but it's easily avoided, so not critical.

---

### Post by Bre Ntt on 2011-06-10
How did you even get it to be recognized? I can't find any drivers for it anywhere? 

Ubuntu 10.04 LTS Lucid Lynx

---

### Post by Perfect Storm on 2011-06-10
Necromancing. Thread closed.

---

