---
title: "Lost graphics resolution using ati 9200 SE"
date: 2009-03-23
forum: General Help
---

### Post by CoximusPrime on 2009-03-23
Hi guys,

  I'm having a very strange problem which I don't even know where to start to fix (I'm pretty used to using Ubuntu on a day to day basis but not enough experience fixing issues yet). Basically my situation is this:

  I'm running an ATI Radeon 9200 SE in Ubuntu 8.04 Hardy Heron (fully upto date) with an LCD monitor. I've been running this for months now with no issues at a resolution of 1280x1024. A couple of days ago however, I booted and my resolution had dropped from my usual 1280x1024 down to 1280x800 .... which I thought was odd seeing as though I don't have a widescreen monitor.

  I went into System -> Preferences -> Screen Resolution and attempted to put the resolution back to 1280x1024, however this is no longer available. So I'm running now at 1024x768 (the largest non-widescreen resolution I can select).

  I haven't installed any new software, only updates, which I can't remember what they were, I just allowed all updates an installed blindly.

  I don't know if this is related and will help diagnose the problem, but since the resolution change, when I open Nautilus (2.22.5.1), it opens full screen and blocks access to the menu bars. 

  Does anyone know what could have happened and how to fix the problem?

  Cheers everyone.

---

### Post by CoximusPrime on 2009-04-01
Hi,

  I've been playing around to try and fix this still ... here's what I've found so far. 

  For some reason it is a problem that has developed between my ubuntu machine and my monitor. If I plug the system into a different monitor, it detects the new monitor fine and determines the highest resolution correctly.

I then came across this link [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) which pointed me in the direction of this solution:

  Connect my monitor I'm having problems.
  Open a terminal
  enter the following

  xrandr --newmode "1280x1024"   90.75  1280 1328 1360 1440  1024 1027 1034 1054 +hsync -vsync
  
  xrandr --addmode VGA 1280x1024

  xrandr --output VGA --mode 1280x1024 --rate 60

and all is well again with the world (atleast until I restart).

I know I can generate a simple script to do this, and that I can run it from the .xprofile file for my user account, but to me the better solution would be to have this done in the gdm.conf file. Only problem is, I don't know how. The above link states that you can just put the xrandr commands in there, but this screws up when I do so and I have to get back in and and remove the lines I entered.

  Does anyone a way to get these commands into my gdm.conf setup??

  Cheers everyone

---

