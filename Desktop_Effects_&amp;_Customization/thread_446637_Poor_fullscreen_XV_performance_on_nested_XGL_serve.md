---
title: "Poor fullscreen XV performance on nested XGL server"
date: 2007-05-17
forum: Desktop Effects &amp; Customization
---

### Post by judoka9999 on 2007-05-17
Pardon the length of this post, I'm going to try to give all pertinent details.
I have recently installed Feisty Fawn with XGL as an additional GDM session (running as display :1, nested). I was first running compiz and have now switched to beryl. I am using the fglrx proprietary drivers on a:

ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

I have noticed poor performance in mplayer and totem under full screen Xv in both compiz and beryl. Desktop effects work, I have fgl_glxgears working fine on display :0, xvinfo shows up properly on both display :0 and :1.

My cpu usage is low when I use display 0 (which has no window manager, so the vid stays in the center of my screen and I can not move it):
mplayer avifile.avi -display :0 -vo xv -fs
Running the same command under display :1 puts my CPU at almost 100% usage.

I have done a good amount of searching on the forums and google and have tried Xgl with both -accel xv:pbuffer and -accel xv:fbo and notice the same issue either way. I have also tried -vo gl2 and see roughly the same high cpu usage in full screen. I had to change to -accel glx:fbo to avoid Xgl crashes. Since changing to -accel glx:fbo running glxgears (not fgl_glxgears) on display :1 will crash the X server and bring me back to a GDM login.

I am attaching my xorg.conf, in case its useful.

Is this performance issue a result of running Xgl as a nested X server? Will it improve if I run Xgl directly from GDM? Is this a known issue with Xgl, and I just need to wait for a fix? Or is it none of the above?

Thanks for your time,
Judoka

---

### Post by judoka9999 on 2007-06-01
On advice form crdlb at #ubuntu-xgl on freenode I stopped using the fglrx driver and XGL and started using the open source radeon driver and AIGLX. It had been awhile since I had used the open source ATI driver, and I didn't know that fullscreen Xv would work from mplayer. While the way beryl handles Xv windows is less than perfect, I can do fullscreen Xv w/ hardware scaling, and its much better than using the fglrx driver and XGL.

I think its worth noting that XGL is not the only way to get desktop effects and the desktop cube. AIGLX gives those abilities to the regular Xorg server and you can still run compiz/beryl w/out XGL.

I followed this tutorial w/ a few differences:
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

First, I used the restircted drivers manager to uninstall fglrx. I still had to manually edit xorg.conf. Also, I use a script set to run in my gnome-session properties to start beryl.

Anyone running the 
 ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
w/ feisty fawn should use the radeon driver w/ AIGLX, and not fglrx w/ XGL. The performance difference is night and day.

Please Note: All that being said, only mplayer will work w/ Xv after you switch to AIGLX. Totem, etc should be set to use X11 and not Xv. This effectively forces totem and other players to do video scaling in software, and not use the graphics hardware.

When/If ATI/XGL fix the performance issue, I hope someone will post that info here so that we can stay up to date. I do prefer the way fglrx handles Xv, but I have also been told the open source driver will soon overtake fglrx in that regard anyways.

Judoka

---

