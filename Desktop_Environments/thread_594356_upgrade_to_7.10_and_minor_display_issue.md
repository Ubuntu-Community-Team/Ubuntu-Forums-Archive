---
title: "upgrade to 7.10 and minor display issue"
date: 2007-10-27
forum: Desktop Environments
---

### Post by jcs3rdma on 2007-10-27
New to the forum any help would be appreciated. Searched and found nothing that appears to apply, so I thought I might ask:

Upgraded from 7.04 to 7.10 and no major problems. Under 7.04 desktop display was fine with my ATI 9800 pro gc. After network upgrade to 7.10 all seems fine, except the desktop display has shifted left about 1/4 to 3/8 of an inch. 
Cannot find any way to put is back. Nothing custom installed or configured.
The defaults were great in 7.04, so I didn't think that I had change anything 7.10.

Thanks for any help.

---

### Post by ohzopants on 2007-10-30
By default 7.10 uses the restricted drivers for your video card.  What type of drivers were you using in 7.04?  This sounds to me like it is either a driver issue or a refresh rate issue.

To check if you are using the restricted drivers go to System -> Administration -> Restricted Package Manager.  To check your refresh rate you should check out your xorg.conf (locate in /etc/X11).

You may also want to try changing the settings on your monitor.

---

### Post by l33t_3lv3n_g33k on 2007-10-31
> You may also want to try changing the settings on your monitor.
 
I second that.  My LCD monitor has an "Auto Adjust" button for this very issue.  CRTs usually have knobs or a menu for horizontal and vertical positioning.

---

### Post by jcs3rdma on 2007-11-04
Thanks bot for your replies:

Drivers?
For 7.04 I was using the default. I didn't check what that might be since everything was just fine. I didn't have to adjust anything.
For 7.10, I have checked and the restricted drivers are NOT selected. 
If I do select it and it makes matters worse, will it be easy to get it back to the current state?

xorg.conf?
The refresh rate appears to be correct. It appears that the xorg.conf may be the original, unmodified, file that was created when the operating system was first installed. That is if the - last changed - info, in the file properties is what I believe it to be. 

This is a dual boot machine and I would prefer not to have to adjust the monitor for each OS. I was just hoping that it would keep the same settings/conf that 7.04 had when I upgraded to 7.10. Well I was hoping anyway.  

Is it normal for the screen postions/orientation to change with each upgrade?

Any other thoughts? Thanks.

---

### Post by ohzopants on 2007-11-06
Enabling the restricted drivers will most likely make things better, not worse.  If it does not it is rather easy to go back.  I would definitely try it.

---

### Post by scochran on 2007-11-08
I am having the same (very similar, anyway) problem...
I upgraded from Feisty to Gutsy, and everything works fine, except the screen position.
The login screen is fine (not sure what resolution it's at), but as soon as X loads up at 1680x1050, the picture 'jumps' about 1.5" to the right.
I can bring it back with the 'auto config' function on the monitor (Westy LCM-22w2), but then the login screen, other resolutions (in gaming), and all WINXP screens (dual booting) are shifted until I hit the auto-config again.
I am using the restricted drivers from Nvidia, just as I was in Feisty.  
This problem did not occur in Feisty, it just started with the upgrade to Gutsy.

I seem to remember reading something about the edid not being read correctly when Gutsy was still in development, but I can't find any reference to that now.

The knee-jerk reaction in the forums (and on the irc channel) seems to be to blame the nvidia drivers, but this problem, as i said, did not appear in Feisty at all with the restricted drivers.

It wouldnt be worth mentioning at all, except that the 'auto config' also resets my brightness, sharpness, and contrast, which must be re-set every time I switch modes.

[edit] Just to clarify:  This 'shift' only happens at 1680x1050 in gutsy; all other resolutions are centered in gutsy, and all resolutions, including 1680x1050, are displayed correctly in WinXP.

---

### Post by jcs3rdma on 2007-11-09
Thanks all!
I have enabled the restricted drivers and the screen/desktop is now back in it's original position. I have not tried any intense graphics display, but for general use, it is just as before.

Thanks once again.:)

---

### Post by HydrantHunter on 2007-11-11
I'm having a similar problem - my screen is shifted to the right about 30 or so pixels (rough guess) when using the apparently correct video driver and setting the screen to Generic 1024x768 LCD.  When using the generic PnP display driver and generic monitor setting I only get 800x600, but the display is perfectly centered.

I checked the restrictred drivers manager and it says my system doesn't need any restricted drivers.  Should I believe it or should I start googling?

My system is a Toshiba Portege 3500 Tablet Notebook - CyberBlade 32MB video, 1024x768 built in LCD (thus no 'auto' anything buttons or screen adjustment at all).

I've been working on this in another thread:
[http://ubuntuforums.org/showthread.php?t=256169](http://ubuntuforums.org/showthread.php?t=256169)

Does this seem like the same issue?

---

### Post by Neilor on 2007-11-20
Similar problem on an ATI 9250 card... GDM screen perfect, login to Gnome ... first time login can sometimes show the correct position but I'm guaranteed to have the screen shift and inch to the left if I logout and log back in.... the whole time the GDM screen is fine.

Running with the open-source drivers, I'll try the restricted driver tonight, but it seems to be an issue with Gnome 2.20 rather than the graphic drivers.

---

