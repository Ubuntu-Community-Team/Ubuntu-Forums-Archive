---
title: "Issue with Dell D630 (nvidia graphics card) and dual montiors"
date: 2007-12-05
forum: Dell  Ubuntu Support
---

### Post by farazkhan on 2007-12-05
Hi all,

I switched over to Ubuntu couple of months ago, and I'm really happy ( I should have done this before)
But i have a problem that I can't solve, i have searched everywhere but couldn't find a solution which worked for me.

Ok so here the issue

I have a Dell Latitude D630 with Nvidia graphics card, and i have couple of Dell E228WFP monitors hooked up with my docking station (one thru DVI and other thru VGA)

I have Ubuntu Gutsy installed (along with Win-XP)

My monitors work fine in windows but when i boot Ubuntu they don't work. As soon as X starts the display goes off, i have to open the laptop lid to login and use Ubuntu.

Can anyone help me solve this problem, i'll appreciate it very much.

Thanks -

Im attaching my xorg.conf file just in case if someone wants to look at it

---

### Post by farazkhan on 2007-12-06
Figured it out, had to download nVidia drivers from their website and using nvidia-setting setup the X server.

---

### Post by phamtuan on 2007-12-07
> **farazkhan said:**
> Figured it out, had to download nVidia drivers from their website and using nvidia-setting setup the X server.

I have the same problem. Thank for the tip. However, the key Fn-F8, which normally would switch from LCD display to CRT or both, does'nt work.
Thus if I want to also display the computer screen on a beamer, I have to connect it  to the computer before the xserver starts. Have you got this problem ?

---

### Post by farazkhan on 2007-12-07
No i haven't got that problem, I tried using Fn-F8 key and it didnt worked for me either.

---

