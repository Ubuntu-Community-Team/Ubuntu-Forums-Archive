---
title: "Compiz Fusion Update Glitches"
date: 2007-09-06
forum: Desktop Environments
---

### Post by circuz_phreak on 2007-09-06
I've read some other posts and am aware some other people are having the same problem.  I installed compiz fusion and had it working properly, updated it a couple days later and lost the functionality of the 3D and Atlantis plugin.  To my knowledge, every other plugin seems to function normally.  Do I just have to sit and wait for a new update that will fix the problem?  Is there a temporary fix I could apply?  Any information or help would be very much appreciated.  Thanks

---

### Post by SigmundL on 2007-09-06
Installed an update yesterday, broke compiz fuzion for me. It just hangs. Using repo [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy-amd64

Anybody else?

---

### Post by gtrtx on 2007-09-06
My problem is with 3d windows and Atlantis. Everything else seems to be fine. 

I don't use Atlants, but would like the 3d windows to work. I suspect that we'll just have to wait it out. 

I have found that it is possible to revert to a previous working version as all the packages are stored in /var/cache/apt/archives. You have to remove the existing version first. Installing the older version is kinda tricky as you have to do it in a particular order due to dependencies. It won't install out of order so you have to use trial and error.

---

### Post by BoogieKnight on 2007-09-07
I had similar issues using the install / compile script that's on this forum. Had it update my already installed (using the same script) compiz only to discover that almost half the plugins were not working anymore. I ultimately fixed it be manually removing every instance of compiz off my system and re-installing / re-compiling completely using the script... now everything works for me again.

btw- in order to completely remove every trace of compiz i had to do a "locate compiz" in terminal and found files all over the place.

don't know if this will help you or not but it worked for me.

---

### Post by gtrtx on 2007-09-07
I have tried the install script several times now, and never with positive results.

Last time I tried to use it the results where disastrous. 

I haven't done "locate compiz" yet, and used the script. I may try this.

However, it's working for the most part, so I may just leave it be.

---

### Post by Inxsible on 2007-09-07
What repos are you using ?

Trevino's repos have all the latest plugins.

Amaranth's repos are  a little behind on the plugins

---

### Post by gtrtx on 2007-09-07
I'm using Trevino's 64 bit repos.

I've kept it up to date, however, my 3d windows and atlantis aren't  working. In fact they can' t even be enabled.

---

### Post by RebounD11 on 2007-09-07
I had some problems with Compiz Fusion updates... everything works fine... from time to time. Sometimes my panels disappear (1 or both), sometimes kiba-dock freezes, sometimes the settings reset themselves.

I have to restart compiz several times until it works properly :|

---

### Post by Inxsible on 2007-09-07
> **gtrtx said:**
> I'm using Trevino's 64 bit repos.

I've kept it up to date, however, my 3d windows and atlantis aren't  working. In fact they can' t even be enabled.
When was the last time you updated? I did an update last night and it works.

you can force an update by doing ```
sudo apt-get update
``````
update-manager
```

---

### Post by circuz_phreak on 2007-09-07
I'm going to try and force the update, but I probably won't have to since its been a couple weeks since last update, or longer?  Anyways, I don't really wanna do a re-install or anything, especially if I can just wait it out for an update.  Having said that, if waiting it out takes forever I might try reverting back to before I updated it.  Can anyone leave a detailed step by step so I don't mess everything up?

P.S. I configured compiz to run on system start, is there a terminal command to stop it from running?  I will probably configure it as a toolbar button to make things easy.

---

### Post by gtrtx on 2007-09-07
> **Inxsible said:**
> When was the last time you updated? I did an update last night and it works.

you can force an update by doing ```
sudo apt-get update
``````
update-manager
```

I'll give that a try. I pretty much update when a new update becomes available. 

Are you using the 64 bit repos?  Does anybody know if the 64 bit repos are updated at the same time the 32 bit ones are?  Seems like I read somewhere that they are slightly behind them. 

It's really not a huge deal, I'm more concerned that the plugins that provide functionality work properly(which they do).  Of course I guess functionality can be subjective. 

I think once I have everything working just as I like it, I'll just stop updating until Gutsy final is released

---

### Post by sr20ve on 2007-09-07
I'm having a similar issue. I've had Compiz configured and running fine for some time until about a week ago. I beleive it was due to a bunch of compiz updates that were installed.

Now all my compiz effects are really slow and choppy, in the meantime, I've switched to beryl and everything is fine.

Unless there's a fix, I'm just waiting for another update to come out that will fix this.

---

### Post by circuz_phreak on 2007-09-09
After I forced the update it fixed the plugin issue, but now like the previous posted, everything is slow and choppy.  Ran alot smoother before, i running a 256mb Nvidia GeForce (8600 GT i think), and a dual-core 2.0ghz with 2gb of ram.  I shouldnt be having this problem....any news on the terminal command to stop compiz from runnning?

---

### Post by munozdj on 2007-09-10
Hi, I´m having the same problem. I´ve recently installed compiz fusion and the cube runs well, but when I minimize any window it drops its fps... sometimes it doesn´t even show the effect.
I´m running ubuntu feisty with kde in a dell inspiron 1520, core 2 duo 2.2GHz and nVidia GeForce 8600M GT. I think this configuration should be enough for compiz fusion to run smoothly. The nVidia drivers are version 100.14.11.
Thanks!

---

### Post by SigmundL on 2007-09-10
> **SigmundL said:**
> Installed an update yesterday, broke compiz fuzion for me. It just hangs. Using repo [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy-amd64

Anybody else?

Solved - the problem was in gnome-compiz-manager. Removed it, everything works.

/S

---

### Post by nille on 2007-09-13
I see that more people seems to have some performance-issues with the 8600-cards. I'm running CF on a 8600M GT and it works great for some minute, then suddenly the fps drops **a lot** and usually ends up at about 5fps..

Sometimes (if I stop rotating the cube?) the FPS goes up to 30 (normal: 60) but sometimes it stops at 5. It also seems like the process compiz.real uses >60% CPU..

**EDIT:** Testing with  --strict-binding and --indirect-rendering seems to have solved the problem.

---

