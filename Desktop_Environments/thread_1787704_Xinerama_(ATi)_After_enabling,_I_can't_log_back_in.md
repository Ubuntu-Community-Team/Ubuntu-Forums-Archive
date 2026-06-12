---
title: "Xinerama (ATi) After enabling, I can't log back in."
date: 2011-06-21
forum: Desktop Environments
---

### Post by Tillman32 on 2011-06-21
I'm using Ubuntu 11.04 - an Acer Aspire 7552G-5430 with an ATi 6650M. 

I can enable dual monitors on an extended desktop, but once I enable Xinerama ( I need this to be able to drag windows between the two screens ) I'm prompted restart to apply the settings, after restarting, I try to log in, I type my password in, hit enter, the screen goes black, and then it goes back to the log in screen. 

Any ideas?

Thanks for your time.


Oh! I forgot to add that I can log into safe mode.

---

### Post by weiteh on 2011-07-03
I am having the same issue. I installed Ubuntu natty with ATI catalyst 11.6. After turning on Xinerama under Display Options, a restart of the system would not let me log back in. The screen goes blank for a few seconds, then the login screen comes back again. I can only login with failsafe gnome session. 
Any idea why this is happening? Or at least, where to begin to debug the problem and possible solving this problem?

---

### Post by djdrey on 2011-07-04
I'm getting exactly the same behaviour. Brand new Dell Optiplex 990 with ATI Radeon HD 5450 gfx card. Turning off Xinerama allows me to login again.

I am seeing in the syslog (not sure if it's related)

Jul  5 10:16:31 MYMACHINE gdm-session-worker[1109]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

---

### Post by Guntotingbastard on 2011-07-08
*bump*

---

### Post by djdrey on 2011-07-08
OK - so I found disabling the ATI driver and going back to the open source drivers provided with Ubuntu solved this problem for me. The standard drivers allowed me to use dual screens and extend the desktop across them both, so it was all good.

---

### Post by danep on 2011-07-13
Yargh... I've also hit this bug. Logging in in safe mode and disabling Xinerama fortunately fixes it. I'd still like to be able to use the proprietary (fglrx) drivers though, because the open-source radeon drivers produce weird artifacts and don't have 3d acceleration. Any suggestions?

---

### Post by gcoram on 2011-10-13
Yep same here. Fully updated Natty. Dell XPS Studio
Native drivers dont give me the resolution options for my desktop monitor even though its only 1280x1024. ATI driver does give the resolutions but....
cant login after enabling xinerama in catalyst.
ctrl-alt 2 - 
sudo aticonfig --xinerama=off 
enabled login again. or select no effects off the login options

Really used to using extended desktop. Is there a way ?

have log errors above as well but this seems more relevant and happens when xinerama enabled.
Oct 13 17:55:27 XPS kernel: [  130.583632] Xorg[2356]: segfault at 88 ip 000000000045fb34 sp 00007fff89580ec0 error 4 in Xorg[400000+1d4000]

Xinerama works fine if logging in with ubuntu classic (no effects). So its the combination of compiz and ATI drivers and xinerama that is the problem.

---

### Post by gcoram on 2011-10-13
ATI Radeon cards as per dell XPS and Natty ubuntu.

Ok after mucking around heres what I got.

Compiz (needed for the default unity 3d) and ATI Catalyst are a no go . Segfaults on log in and other troubles. :(
With the native drivers some resolution modes are not being detected at least on some monitors. This is fixable. 
eg
sudo xrandr --newmode "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060
sudo xrandr --addmode VGA-0 "1280x1024_60.00"
then monitor preferences is good to go.
You still need to make this permanent which tricky because most docos around tell you to add to xorg.conf which no longer exists. This should be easy to solve though.

However if like me you use 3d software like blender you will find it is so slow as to be unusable with the native drivers.
So back to ATI drivers and install unity2d to avoid the compiz clash and thats as good as it gets. 

Which is still pretty bloody good really ;)

Will upgrade to oneiric tonight but not expecting that to solve these issues. Ubuntu and Unity is still excellent even in 2D.

---

