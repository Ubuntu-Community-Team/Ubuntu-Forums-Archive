---
title: "Multi Monitor issue"
date: 2010-05-07
forum: Desktop Environments
---

### Post by darkenvy6 on 2010-05-07
I just recently got my nvidia drivers to work and multi-monitoring to show up. I'm thrilled :D! But something odd happens.... I can mouse over and drag windows to the monitor on the right but if the mouse even just touches the border of the monitor on the left then the system freezes while the mouse glitches between 3 points constantly (really fast). At this point Ctrl Alt F1 not Ctrl Alt Delete or anything else will work. It doesn't even look like I have an influence on the mouse on the screen. 

What do you think?

---

### Post by paulisdead on 2010-05-07
If you're on Lucid, which drivers did you install?  I'm using the ones from the nvidia-current packages, to get a 195.xx driver.  Dual displays have been working fine on both my desktop with an 8800GTS, and my laptop at work that has some sort of mobile quadro card, I forget the model.  When I was on Karmic, I'd either install the drivers from nvidia's site or just use the vdpau ppa, even though I didn't have a card that supported VDPAU.  In karmic the repo gave me a set of 195 drivers, plus more up to date versions of mplayer/smplayer.  Hopefully they've fixed your issue in a newer driver.

---

### Post by darkenvy6 on 2010-05-07
nope Im in Lucid with the drivers from the nvidia-current package. I had issues installing that package (took more than 3 times of installing Lucid to get it to work) and here is what I also had to install to not get it to fail altogether:
> 
**Modaliases for the NVIDIA binary X.Org driver**[I]
nvidia-current-modaliases
[/I]
**Transitional package for nvidia-185-libvdpau-dev**
nvidia-185-libvdpau-dev

**Tool of configuring the NVIDIA graphics driver**
nvidia-settings

Then installed the **NVIDIA accelerated graphics driver (version  Current)** from "Hardware Devices"
my previous thread:
[http://ubuntuforums.org/showthread.php?p=9258022#post9258022](http://ubuntuforums.org/showthread.php?p=9258022#post9258022)


Thanks for your help!

---

### Post by kbin on 2010-05-11
I have the exact same issue with the mouse locking up, flickering and moving between three places really fast... 

But i've noticed it only happens when i enter a screen that is laid out ABOVE the "main screen"... if i arrange the screens so that all four are in a row, it works fine. But as soon as i arrange so that two screens are above my main screen (as they are arranged physically) then when I move the mouse from the main screen to the one above it, it enters this strange state. 

Sometimes it is possible to move down to the main screen again and sometimes the mouse is stuck there forever.

But if I arrange the screens all in row or that two screens are below my "main screen" it works...

I have tried downgrading the nvidia driver, but then X won't even start...

Facts:
Lucid Lynx
Graphic adapters 2 x GeForce 8400
4 monitors: Main Screen 1920x1200, One 1600x1200 (to the right) and two 1280x1024 physically mounted above the two bigger monitors
Driver nvidia-current (195.36.15-0ubuntu3)
Xinerama: yes
[EDIT] Just saw "kubuntu" in subject line... i'm running plain Ubuntu with gnome and have the same problem... [/EDIT]

All this worked fine in Karmic, but there Xinerama seemed to slow things down when having >2 monitors making it not usable for me (running several virtual boxes in fullscreen was the issue), that however seems to work much better in Lucid... now this however... :-(

//Kalle

---

### Post by darkenvy6 on 2010-05-11
> **kbin said:**
> 
Just saw "kubuntu" in subject line... i'm running plain Ubuntu with gnome and have the same problem...
//Kalle
Yes I would change that if I could now.

 I now tried this on ubuntu with gnome and lubuntu with the LXDE and have the same problem. Wierdly enough all 3 of my monitor are side by side and my middle and primary monitor is the largest. only when going left does it happen to me. It seems the problem may reside in ubuntu.  Regardless if it is an issue I'm not switching because of this problem. I'll keep you posted on the investigation.

Edit: oh BTW, using Ctrl-Alt-Del seems to bring you back to the KDM. Useful for experimenting and not having to reboot.


[B]Update:
[/B]I arranged my monitors accordingly and have no problems. Of course this isn't ideal. I'm still workin on it.
In this situation my GTX295 coop is GPU1 and GPU2. The 9800GTX is GPU3
 Main-monitor/GPU1 -> right-monitor/GPU3 -> far-right-monitor/GPU2

  Although my middle monitor must be main. (and not just changing taskbars ect, I need this to be on my GTX295)

---

### Post by darkenvy6 on 2010-05-16
bump

I really need some help! I can't get any further :(

---

### Post by darkenvy6 on 2010-05-26
Not meaning to revive old threads but for documentation purposes I am stating what I found.  From what I can *speculate*:

The reason why the mouse glitches out (from what I can figure out) is caused when you arange your monitors. The main monitor must be the top-left most monitor. If any monitor goes to the left or above would result in some sort of -0,-0 coordinate of the mouse. I guess it trips it up. This also ties into which ports you arrange the monitors in too. I figured I would be able to solve the problem if I made my left monitor the primary and string to the far right but the "Samsung" remains the main. 

Arranging monitors as:
[1][3]
[2]
to avoid the problem.


Now how do I submit a bug report so this can be addressed finally?

---

