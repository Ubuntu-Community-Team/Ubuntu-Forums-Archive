---
title: "Parachute Deployed"
date: 2005-05-10
forum: Gaming &amp; Leisure
---

### Post by jon_hill987 on 2005-05-10
I have installed Mutant Storm (demo) on Ubuntu. When I tried to run it I got errors about missing lib's. I have now installed all of the libs it wanted but it stil wont run. I get a fatal error: Segmentation Fault (SDL Parachute Deployed). GL must be working on my system as all the GL screensavers work fine. What am I missing?

---

### Post by JonahRowley on 2005-05-11
It's very difficult to say what's wrong, other than "it crashed."  If you have any programming skills, try enabling core dumps and see where the program is crashing.

Mutant Storm doesn't have a static build?  That would simplify things a bunch, and it's often how closed-source games are distributed on Linux.  Dynamic builds must be maintained as software versions advance and as interfaces change.

---

### Post by jon_hill987 on 2005-05-11
Thanx for the adcice. I have a little programing knowlege, how do you go about enabling core dumps?

---

### Post by lunadog on 2006-07-04
I have just managed to fix this problem.. (sorry for restarting a thread that is a year old but I can't post on the pompom forums as they are locked).

1) copy the libSDL-1.2.so.0.5 to /usr/local/lib
2) as root run ldconfig
3) move /usr/local/lib/libSDL-1.2.so.0.5 and /usr/local/lib/libSDL-1.2.so.0 back to the MutantStorm folder
4) edit mutantstorm in the mutant storm folder and add the following line (near the top perhaps line 8 or so):

LD_PRELOAD=libSDL-1.2.so.0

5) It should now run.... I had an additional problem with it not creating an mcop directory for me and I fixed this with:

mkdir ~/.kde/socket-$(cat /etc/hostname)

Then mutant storm runs fine!!!!

WOW!

James

---

