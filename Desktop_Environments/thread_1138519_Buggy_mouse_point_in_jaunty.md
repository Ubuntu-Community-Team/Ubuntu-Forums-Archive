---
title: "Buggy mouse point in jaunty"
date: 2009-04-26
forum: Desktop Environments
---

### Post by ZeldaFan on 2009-04-26
When setting up dual screens with an nvidia graphics card (the latest 180.44 drivers), I use the separate x screen options. When moving the mouse between monitors, while the mouse moves to the other screen, a remnant of that pointer remains in the other screen. Why is the mouse still showing up on that screen?

This problem didn't exist on intrepid but it does in jaunty, so any help would be appreciated.

---

### Post by rockrman on 2009-04-28
I've exactly the same problem.
Nvidia 8400gs with NV drivers 180.44 (latest beta 185.18.04 gives me kernel panic while switching hdmi output)

There's a similar bug report here (second paragraph):
[https://bugs.launchpad.net/ubuntu/+bug/366743](https://bugs.launchpad.net/ubuntu/+bug/366743)

---

### Post by ctrlER on 2009-05-04
Exactly the same problem here, the pointer freezes at the edge of the screen and a new one appears on the other screen. Using nvidia-glx-180.51-0ubuntu2 in 32bit architecture.

---

### Post by ZeldaFan on 2009-05-07
has anyone found any solutions to the problem yet?

---

### Post by ipsi on 2009-05-24
Same here. Looks like I've effectively got two mouse pointers or something. I note that when I upgraded, the mouse/keyboard sections of xorg.conf were commented out. Could it have something to do with that?

Anyway, merely a graphical glitch at the moment, rather than something serious. Hope there's a solution out there though...

---

### Post by asmoore82 on 2009-05-24
There are some advanced xorg.conf options for hardware pointers specific to Nvidia - I can't quote them from memory.

Also, maybe Nvidia's hardware cursor is in a tug of war with compiz "Desktop Effects"
On my Intel VGA, "Enhanced Desktop Zoom" with the "Scale the mouse pointer" and
"Hide original mouse pointer" options both enabled is a big No-No.
it causes a "magic disappearing mouse pointer" whenever zoom is *not* in use.

---

### Post by rockrman on 2009-07-06
Does anyone solved this problem?

thanks

---

