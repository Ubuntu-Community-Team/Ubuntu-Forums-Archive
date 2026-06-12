---
title: "Dell Latitude D830 Ubuntu 7.04 -not possible to start X server"
date: 2007-06-17
forum: Dell  Ubuntu Support
---

### Post by No_good_names_left on 2007-06-17
Hi all, 

I'm a complete beginner so please don't baffle me with high tech terms. I recently bought a Dell Latitude D830 and believed it would be a simple matter to install ubuntu 7.04 as I had heard from others, unfortunately no.

At install of desktop there is the message "failed to start the X server". The graphical interface dosn't start and exits to a command line. There is a reference to logfile /var/log/Xorg.0.log and config fie etc/X11/xorg.conf. Looking in the files it seems the error is that no screens are found.

Having read all that I could find so far, it seems there are other posts indicating that the problem is that the current distribution dosn't contain the correct Intel drivers for the GMA X3100 (
Mobile intel GM965 express chip set) video card.

I have read other posts that say I can fetch the drivers and recompile the kernal and I'll be OK but it's all technically beyond me. By using the alternative install CD I have managed to install ubuntu via text install but until I can get the graphical interface working I'm not sure how I can proceed.

I would just like to ask if anyone has managed to install the standard distribution on Dell D830 and if the had the same problems. If there is a step by step easy way to continue from here I would certainly like to hear about it.

I know I should be sending logs and the like but as I dont even know any linux commands I'm not sure how I can even get them out. I imagine I should be able to somehow access my USB devices from command line?

---

### Post by coppertrail on 2007-06-17
The same thing happened with my Inspiron 6000 (ATI X300 Mobility).  It's been running fine for weeks, this started after the last round of updates. I'll look into this further when I get home this evening.  I am running the ATI drivers in accelerated mode, which may be part of the problem.  

The problem is definitely in the xorg.conf file. On mine, it's not dumping me to a command prompt.  

I'm going to rename my current xorg.conf file and replace it with a backup version; hopefully this will at least let me into X so I can compare the 2 files.

---

### Post by No_good_names_left on 2007-06-18
Hi a further update.

I have found a tempory solution, credit goes to "groovy guru" I tried his fix from another similar problem. it was as follows:

"The problem is the screen resolution. I have a 1920x1200 screen. However 1280 x 1024 will do the job.

Now at the command prompt run the command

sudo dpkg-reconfigure xserver-xorg

This will run through some rigmarole which you can just except the defaults for except for two things. When it wants the video driver pick "vesa" , second when it asks what res pick 1280x1024.

Now at the command line run

sudo /etc/init.d/gdm start

That should get the live CD fired up with the wrong screen res." 

Now I have graphical interface of a sorts I just need to work out how to get the correct resolution.

---

### Post by coppertrail on 2007-06-18
Glad you got this resolved.  My issue ended being of a completely different origin, and not related to the updates from last week.  

A few weeks ago, I went through some steps to get the forward/back buttons working on my mouse.  Since then, I'd only used my laptop with my external mouse.  Yesterday was the first time I used it without.  

The xorg.conf file was complaining about not being able to find a pointing device.  I ended up re-installing ubuntu, and I'll live without my forward/back buttons on the external mouse :)

---

### Post by wak_wak on 2007-06-28
Wow!  Thanks a lot!!!!

---

### Post by wak_wak on 2007-06-29
How about the same but with kubuntu?

---

### Post by neptho on 2007-06-30
> **wak_wak said:**
> How about the same but with kubuntu?

Try the same.  Both KDE and GNOME run on the same XOrg server.  :)

---

