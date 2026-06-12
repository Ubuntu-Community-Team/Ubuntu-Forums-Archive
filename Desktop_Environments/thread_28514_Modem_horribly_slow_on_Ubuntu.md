---
title: "Modem horribly slow on Ubuntu"
date: 2005-04-20
forum: Desktop Environments
---

### Post by GTKpower on 2005-04-20
I have dialup.  I'll admit it, lol.

But I got the most out of my 56k modem on PClinuxOS, running KDE.  Download speeds were a respectable (for a 56k) 5000-6000 bytes/second.

Although Ubuntu 5.04 is great for me so far, download speeds and repository-loading speeds are horribly slow.  I'm averaging anywhere from 0.93-400 bytes/second.   Took me 6 minutes to download a 430k file from gnome-look.org.

What's causing this?  Is something else running in  the background?  Ever since I installed Ubuntu last night it's been slow.  I couldn't even load the repositories properly..  I certainly don't see anything taking up my bandwidth.  I'm connecting to the net using Network Connections - a regular ISP hookup.  I've tried pp0 and lo (?) without improvement.   I used to use kPPP.  Funnily enough, Network Connections doesn'rt save my preferences once I exit it.  I keep having tp input ISP phone # and my username every time I want to connect.   

Any ideas?

---

### Post by josel on 2005-04-20
Modem speed is entirely a matter between the physical modem and the dial-up pool.... that is until softmodems came along. If you got an external modem then nothing to do with the OS, if you have a softmodem then there is a chance. Take a look at connect speed and "freeze" max speed to that (you wont do better anyway). This is done normally with +MS=V90,,,,,max_speed - take a look at your modem manual for how. 
A quick test would be to add four (4) commas (,) after dialup number , sometimes five commas - this makes the modem ignore V90/V90 negotiation and forces it to V34 (max speed 33600 bps). If things are very fast then do the above. Good luck.

---

### Post by GTKpower on 2005-04-20
I have a US Robotics external hardware modem, 56k.

So you're saying, that by inserting those commas after the dialup number, I can enusre that the modem runs at its top possible speed?

I used to use kPPP.  Maybe that was a bbetter dialup tool than what GNOME has to offer right now?  I remember I had LOTS of configuration options with kPPP.  The defaults usually worked the best.

---

### Post by nitsuj on 2005-04-20
Try following the instructions listed in comment #3 (worked for me!) from:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8890](https://bugzilla.ubuntu.com/show_bug.cgi?id=8890)

---

### Post by GTKpower on 2005-04-21
Thank you kindly for all the replies!!  Wow, very nice of you all.  

I just installed GNOME-PPP from these massive repositories that seem to have everything, both GNOME and KDE.

GNOME-PPP is exaclty like kPPP, except that it's GTK-based.  Fixed my problem nicely.  My little 56k moem is now running between 5000-6000 bytes/second, sometimes even spiking at 11 kb/s for a short while.  A fairly respectable clip for a dialup job.

Thanks again!

---

