---
title: "Nvidia + Dell Trinitron Resolution Issues"
date: 2007-05-20
forum: Desktop Environments
---

### Post by mistab1034 on 2007-05-20
I just upgraded from Dapper to Feisty and I am having some issues with resolution on my Dell Trinitron Monitor. After the clean install it only displays at 800x600. I tried installing the nvidia restricted drivers and still only get 800x600. If I plug in another monitor and reconfigure X with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
I can get any resolution I want. 

I never had this issue with Dapper, but when I did the Dapper install I had a different monitor and changing over to the new monitor I didn't give me any problems.

Here are my xorg.conf and Xorg.log files if that helps at all.
[xorg.conf]("http://www.eece.maine.edu/~jbeaulie/xorg.conf")
[Xorg.log]("http://www.eece.maine.edu/~jbeaulie/Xorg.log")

Any ideas are readily accepted.

---

### Post by mistab1034 on 2007-05-21
Update:

I got my monitor to go to full resolution with the default nv driver by installing the 2.6.20-15-386 kernel instead of the 2.6.20-15-generic kernel and changing the monitor in the screen section of my xorg.conf to 'generic monitor'. But I still can't get full resolution with the nvidia restricted driver. 

Another thing I noticed is that with the nvidia restricted driver it looks like the monitor type is getting identified as '@@@', I can't seemed to find anything anywhere about what this means, if it's my monitor messing up or my video card not reading the monitor correctly.

Anyone out there have any similar issues?

---

### Post by satandole666 on 2007-05-21
Now that I figured out to get the nvidia drivers installed properly (at least I hope).  I am having the same issue.  I have an 8800 GTS and a Dell Trinitron P1100 21" monitor.  Same problem.  Any help is appreciated.

---

### Post by satandole666 on 2007-05-21
Anybody?  This resolution is killing me!

---

### Post by satandole666 on 2007-05-21
I think I found a solution.

After installing the nvidia drivers go to System Tools->Nvidia Settings in the Ubuntu Menu.

It allowed me to set 1600x1200 with a refresh rate of 100hz.

I saved that to the xorg config...I'll see if the settings stick after a restart.

---

### Post by mistab1034 on 2007-05-29
I wasn't able to get the Nvidia Settings tool to help me change my resolution. So after trying and failing at installing the latest Nvidia drivers direct from Nvidia's website I'm back to using my Dapper install, but if anyone knows of a solution for this problem I'd really like to use fiesty.

---

