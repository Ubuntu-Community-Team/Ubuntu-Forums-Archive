---
title: "strange desktop / screen resolution issue"
date: 2007-10-26
forum: Desktop Environments
---

### Post by amcink on 2007-10-26
Hi all,

I've been having a problem since installing Ubuntu 7.10. This problem was present when I used to Live CD and also when I did a USB key persistent install using a tutorial. Thought that perhaps the full install might help. I apparentlythought wrong.

It seems I have a desktop within a desktop (screenshot below). I have a Viewsonic VA1930wm monitor that was successfuly detected, as is the video card is ATI Technologies Inc RS480 [Radeon Xpress 200G Series]_ in the xserver-xorg configuration thingy that people have referred to in many of the posts I've read trying to fix this issue.

Under System > Administration > Screens & Graphics, I'm only able to choose 640x480 at 60Hz. Under System > Preferences > Screen Resolution, same thing. The native resolution of my monitor is 1440x900. There's also a black portion on the left side of the screen that is unused.

When I'm using (or at least, trying to use) Ubuntu, windows will go full screen but are grainy with fonts looking all weird and the task bar superimposed on the window.

I'm sure you'll need more info to help me in fixing this problem... issue is, I'm not sure what info that may be. 

xrandr gives this info

Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1440 x 900
VGA-0 connected 1440x900+0+0 (normal left inverted right) 410mm x 260mm
   1440x900       59.9*+   59.9  
   1440x900@60    60.0  
   1280x800@60    60.0  
   1280x768@60    60.0  
   1280x720@60    60.0  
   1024x768       60.0  
   800x600@60     60.3  
   800x600        60.3     56.2  
   800x600@56     56.2  
   640x480        60.0  
LVDS connected 640x480+0+0 (normal left inverted right) 0mm x 0mm
   640x480        59.9*+   59.9

This is what it looks like:

[IMG]http://hubmag.googlepages.com/Screenshot.png/Screenshot-full.jpg[/IMG]

Any insight will be very much appreciate.

Thanks

---

### Post by amcink on 2007-10-26
Apologies for the weird formatting... apparently the screenshot is a bit too big...

---

### Post by amcink on 2007-10-29
I guess no one's heard of a similar problem or resolution (no pun intended)?
Strange... I find it hard to believe I'm the only one who has encountered this problem, though searching the forums for a similar call for help and possible solution net nothing.
If anyone has any ideas at all or if more info is required, I'd be very interested to hear.

---

### Post by debiantu on 2007-10-29
I have a similar problem and will keep an eye on your thread for possible resolutions..  I can get 1024x768 screen resolution.. but both top and bottom panels are at 800x600 resolution.  When I maximize some programs - it only goes up to 800x600.. so what I have to do is go into "unmaximize" state of the program and manually drag it to take the whole screen.

---

### Post by josss on 2007-10-29
Since ATi is already well known for their bad support for linux,i think the problem is screen resolution.

Try to get into the recovery mode in the grub menu.It will brings you to terminal,not X.In the terminal,type this "sudo dpkg-reconfigure -phigh xserver-xorg".It will bring to some options.Select ATI and choose the screen resolution you want.It is easy because all done automatically.

In case,it does not works.You may also can change the screen resolution manually "sudo nano /etc/X11/xorg.conf"

---

### Post by BU5T4 on 2007-12-13
Hi Folks,

I have just installed a fresh copy of ubuntu and have the same issue but i'm not using an ATI card but the Intel 950.

I have had Ubuntu running on this machine numerous times but have never had this issue.

I also have a small screen during login. It's as if the desktop and login doesn't know that it's being displayed at another size and is defaulting to 800 x 600.

if i move the panel to the right hand of the screen running vertically then move it back to the bottom it fills the whole window.

 I have included a screenshot so you can see the issue.

If anyone can help with this issue I would very much appreciate it.

Thanks 

BU5T4:confused:

---

### Post by BU5T4 on 2007-12-14
Any ideas folks?

---

