---
title: "Using 3 monitors. Funny problem."
date: 2010-10-30
forum: Desktop Environments
---

### Post by MarkW7 on 2010-10-30
[SIZE=2]
Using 3 monitors. Funny problem.[/SIZE]

I am running Ubuntu 10.04 and my current setup is;

Motherboard: Asus P5Q Deluxe
Card 1: 8800GTX
Card 2: 8400GS
Monitor(s): 3x 22"

The problem i have is that i can get the two on the 8800GTX to work together but i can only get the one on the 8400GS to work as a "Separate x screen" which is no good because i can't drag windows or anything over to it.

Any ideas?
Thank you.

[IMG]http://markwood.co.cc/donotdelete/nvidia-settings-3-monitor.png[/IMG]

---

### Post by MarkW7 on 2010-11-01
still having this problem. :(

---

### Post by BattleCube on 2010-11-01
im not uber experienced in linux, but i am studying for the comptia linux plus certification and have had a few months of experience with it, and the last few days i have been dealing with a similar problem

as far as i can tell, if you use twinview from nvidia, you can only use groups of 2 moniters (and you cant move screens out of or to a group of 2 moniters) you can use seperate x screens for each screen, (and enable xinerama) to move windows between screens, but then you cant use compiz (for animations and appearance)

ive been trying to figure it out for my own setup of 4 screens, but havent gotten a solution to allow the movement of windows accross all screens AND having compiz ebabled

---

### Post by usagiakumu on 2010-11-01
Should have bought a crossfire board and ATI :-P

---

### Post by kkaldroma on 2010-11-01
I ran into a problem using multiple graphics cards a while back. The issue was due to virtual memory allocation.

I had to:
vi /boot/grub/grub.cfg
and replace 'quite spash' on the kernel line with 
VMALLOC=512M
:
after that the third card stopped crashing.

It's worth a shot and shouldn't cause any problems if it doesn't work.
Good Luck

---

