---
title: "black screen"
date: 2015-05-19
forum: Desktop Environments
---

### Post by drechsel on 2015-05-19
Hi everybody,

my "trusty" (14.04.)  box ran nicely for months, then started not to boot properly, but showing just a black screen. A restart would normally solve the problem.

Now, it no longer starts. I get till the login screen, but whenever I try either to log in as normal user, or as a guest - ever I'm kicked back to the login screen again.

First I got an error message, saying something like:
mtrr: no MTRR for d0000000,8000000 found

So I tried to find out something about MTRR, found the fixmtrr.sh script and ran it. But that didnt solve the problem.

Attached you find dmesg, Xorg:0.log, the result of fwts and the fixmtrr.sh script.

What i cannot understand - why does it show the startup screen, and crashes when a real user is logged in?

NB:
A Linux Mint 17 installation runs without any problem on the same machine. The problem occurs with the onboard graphics as well as with a GeForce100 card.

Any help would be appreciated.
herrdeh

---

### Post by drechsel on 2015-05-22
> sudo apt-get remove --purge xserver-xorg
sudo apt-get autoremove
sudo apt-get install xserver-xorg

did do the job. Machine seems to be back at work.

---

### Post by RobGoss on 2015-05-28
So did this method work for you and is your machine still operational?

---

