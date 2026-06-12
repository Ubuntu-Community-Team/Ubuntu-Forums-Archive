---
title: "New Install, Working X-server but Xorg.conf is Blank"
date: 2009-02-06
forum: General Help
---

### Post by nfox on 2009-02-06
Hey,

I upgraded to Intrepid from a clean Hardy server install and put KDE 4.2 from nightly (no other window manager). I tried to go for the minimal approach with X so I only installed xserver-xorg-core and xserver-xorg-common. This includes the '-input-' extensions but nothing more. 

Unlike any other install I've done yet (and there were many), my VGA output resolution is perfect automatically at login. No randr needed and no flickering even with Compiz at login time. I'm thinking this is the best and cleanest install yet.


But my xorg.conf file is completely empty. It exists, but it's empty. I'm no n00b to Linux so yes, I'm looking at "/etc/X11/xorg.conf" and there's no typos. 

I do not want to install additional packages and all I need is to extend my virtual desktop to get my dual screens one on top of the other. With a blank xorg.conf, I can't add the necessary lines. 

Not only do I want/need to have my LVDS and VGA outputs stacked but I'm going to be adding multi-point to X and will need to meddle around with xorg.conf to do that.

Any ideas?

---

### Post by igknighted on 2009-02-06
Ubuntu has (for most tasks) moved away from the static "xorg.conf" file, and is dynamically configuring X with (I believe Hal?) every time.  Xorg.conf is provided, and you can always build it the way you desire.  And there are tasks it is required for (advanced configuration of wacom tablets, for example).  Whether there is a way to do dual screens without an xorg.conf I do not know (I would suspect this is possible), but you might want to rebuild yours to try multipoint X.

---

### Post by pickarooney on 2009-02-06
If you have an nvidia card there are two tools called nvidia-xconfig and nvidia-settings which should allow you to extend the desktop to a second screen without using xorg.conf. For ATI card there's a hydravision interface for linux I think.

---

### Post by nfox on 2009-02-06
Thanks for the replies.

I see the configuration is in ~/screen-configurations.xml or ~/.local/screen-configurations.xml as they are identical files. I found no reference except for one French site that mentioned the file. I don't see any entry that would indicate support for virtual screen size. Any ideas?

---

