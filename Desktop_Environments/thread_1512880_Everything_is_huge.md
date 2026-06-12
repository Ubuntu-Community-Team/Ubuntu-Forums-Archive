---
title: "Everything is huge"
date: 2010-06-18
forum: Desktop Environments
---

### Post by clayman1000x on 2010-06-18
I have a huge issue, I log into my 10.04 Ubuntu and everything is so huge, how do I lower or raise the resolution to make the desktop smaller, I have a 22" screen and Ubuntu is huge (I can't see the bottom half of the themes page and can't move it up into view), by the way I am new with this Ubuntu environment.

---

### Post by pastalavista on 2010-06-18
System-> Preferences-> Monitors is where you can set the resolution. If you can't see it, try logging in safe graphics mode (the session button bottom of log-in screen) make the changes and log out/back in normally.

---

### Post by clayman1000x on 2010-06-18
These pics should show what I mean.

---

### Post by pastalavista on 2010-06-18
you need more pixels and screen space. my previous post says how... choose the highest resolution listed in the correct aspect ratio

---

### Post by clayman1000x on 2010-06-18
I tried all that, the only choices of resolutions are 640*480 and 320*240, I can't even test the monitor. My monitor is a 22" lcd, I didn't have this problem with 10.04 before. I know this monitor has more resolutions than that.
I am at the highest resolution I can get, I know what I need to do I just can't do it. I usually use 1780* something or somewhere in that neighborhood.

---

### Post by bigsmitty64 on 2010-06-18
All hardware drivers up to date?  On the panel, go to, System/Administration/Hardware Drivers. It will search for the latest drivers for you, when presented with the options choose the latest driver, (usually the recommended). Maybe this will help. Can't hurt :)

---

### Post by clayman1000x on 2010-06-18
> **bigsmitty64 said:**
> All hardware drivers up to date?  On the panel, go to, System/Administration/Hardware Drivers. It will search for the latest drivers for you, when presented with the options choose the latest driver, (usually the recommended). Maybe this will help. Can't hurt :)
I have tried that, I can't see the whole window to make these changes, that is why I put these pics up, the bottoms of the windows is below the taskbar, and I can't move them up, I need an alternative way to raise the resolution.

---

### Post by kerry_s on 2010-06-18
> **clayman1000x said:**
> I have tried that, I can't see the whole window to make these changes, that is why I put these pics up, the bottoms of the windows is below the taskbar, and I can't move them up, I need an alternative way to raise the resolution.

alt+left mouse to move the whole window around.

---

### Post by JuseBox on 2010-06-19
What does your xorg look like?

```

cat /etc/X11/xorg.conf > ~/xorg.txt

```

---

### Post by clayman1000x on 2010-06-19
I does nothing.

---

### Post by clayman1000x on 2010-06-19
> **kerry_s said:**
> alt+left mouse to move the whole window around.
Thanks for that, I can now move the window again but can't seem to raise the resolution. I use an nvidia card 9400. I must have an nvidia driver messing up. I get unknown monitor in Monitor Preferences. can't raise resolution over 640*480 and only one other smaller option.

---

### Post by clayman1000x on 2010-06-19
Thanks for all your help, I fixed it by reinstalling the hardware driver. I can now get all the resolutions available for this screen size. Mark this as solved.

---

### Post by bigsmitty64 on 2010-06-20
Glad to hear you got it going. It was the drivers huh? Cool. I have the same card by the way. nvidia 9400 gt.  I've had it for a while now and I'm quite happy with it overall. Again, glad you got it sorted. :)

---

### Post by clayman1000x on 2010-06-20
> **bigsmitty64 said:**
> Glad to hear you got it going. It was the drivers huh? Cool. I have the same card by the way. nvidia 9400 gt.  I've had it for a while now and I'm quite happy with it overall. Again, glad you got it sorted. :)

I am very happy with that card too. What is funny though is that after I fixed it, went back to windows a while later came back to Ubuntu and the same thing was still there, but a minor change fixed it again. Haven't been on Ubuntu yet today but I will later.

---

### Post by bigsmitty64 on 2010-06-20
I found this in another thread, it may help.
Try this,
Set your rez to what you want, then,

Open a terminal and run:

     
     ```
sudo nvidia-xconfig 
```Then:

     
     ```
gksudo nvidia-settings 
```This should help your settings stick.

---

