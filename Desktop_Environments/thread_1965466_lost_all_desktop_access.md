---
title: "lost all desktop access"
date: 2012-04-25
forum: Desktop Environments
---

### Post by wizkidcom on 2012-04-25
Hi All,
I have the 1204 beta load, and something wierd happened.  I updated to the beta nvidia driver, and after a reboot, I could no longer get a X display, I can't use alt-ctl-Fx to get to a vty, I can get in via the network.

I've used jockey-text to switch back to the old nvidia driver,
I've un-installed and re-installed nvidia drivers. 
I un-installed gdm 
I've run nvidia-configure
I've run dpkg-reconfigure -a

What I find as wierd, is that I can't get to a console terminal.  

  Any ideas on what to check next?

---

### Post by techsupport on 2012-04-25
> **wizkidcom said:**
> Hi All,
I have the 1204 beta load, and something wierd happened.  I updated to the beta nvidia driver, and after a reboot, I could no longer get a X display, I can't use alt-ctl-Fx to get to a vty, I can get in via the network.

I've used jockey-text to switch back to the old nvidia driver,
I've un-installed and re-installed nvidia drivers. 
I un-installed gdm 
I've run nvidia-configure
I've run dpkg-reconfigure -a

What I find as wierd, is that I can't get to a console terminal.  

  Any ideas on what to check next?

They have reported a bug wtih the video drivers. Drop your user to Ubuntu 2D sesssion for now.

---

### Post by wizkidcom on 2012-05-03
I got it solved.  I traced it down to a issue with jocky.  I figured out how to use the cli to point to the proper version of nvidia drivers.  The beta version of nvidia drivers that jocky tried to set up didn't exist.  I ended up re-installing nvidia several times, then it started working automagically.

But now, GDM segfaults.  I had to go back to my mint 11 build because I use the workstation for work, and I've been on-call this week  :(  I'll start looking at getting my new build cleaned up and working next week.

---

