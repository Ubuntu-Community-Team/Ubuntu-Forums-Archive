---
title: "multiseat setup with xephyr under gutsy"
date: 2007-12-12
forum: Desktop Environments
---

### Post by Silby on 2007-12-12
Hi,

I'm trying to set up a multiseat environment under gutsy exactly the same way as i had it working under feisty. The method used can be found at this address: [http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html]("http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html")

At first i bumped into a few problems getting the precompiled Xephyr to work through the script, but after some (very minor) changes, that xephyr with evdev support now happily works. The problem now is getting gdm  to be my friend. It seems that starting the initial Xorg server does not work as described anymore. The config file holds the following to start the X server
[server-base]
name=base
command=/usr/bin/X -ac -br
handled=false
flexible=false

followed by the lines to start the xephyr instances. It seems handled=false is causing the error, but i may be wrong. From reading the log files, syslog tells me gdm: warning: gdm_cleanup_children: child #### crashed of signal 11. Thats the Xorg server starting and immediately getting killed. 

Has anyone gotten the above method to work under Gutsy? Any help would be appreciated.

Regards

---

### Post by tinsami1 on 2008-01-25
gdm is broken.  It can't seem to process handle=false properly.

Loot at [http://groovix.com](http://groovix.com) -- they have a solution.

Or roll out your own by downgrading gdm to feisty -- you may need to recompile for gutsy.  If that's not your cup of tea, go to groovix.com.

I'm not connected or involved in any way with groovix.com, except for the simple fact that I got gutsy to run a Xephyr multiseat with 3 ATI Radeon RV100 cards.

---

### Post by tinsami1 on 2008-01-25
I have to add, from googling around, multiseat in gutsy works only if you have multiple cards because of the xrandr impementation.  I haven't been able to setup a multiseat in Gutsy with only a video card with two outputs (VGA and DVI), yet -- stick to Feisty for this and hope they fix things in Hardy.

---

### Post by serrs on 2008-01-27
Multiseat on one card is only possible by running nested Xs.  You can look at Xephyr...  or I found that Userful.com has a very easy to use (commercial) package for this, even in the gutsy repositories.

---

### Post by tinsami1 on 2008-01-28
> **serrs said:**
> Multiseat on one card is only possible by running nested Xs.  You can look at Xephyr...  or I found that Userful.com has a very easy to use (commercial) package for this, even in the gutsy repositories.

I was referring to Xephyr.  Unfortunately, in Gutsy the two ports in one card can only be used as one desktop -- as far as my trials go with 3 ATI RV100 cards (each with a DVI and VGA output ports).  YMMV with other cards.

---

### Post by Silby on 2008-01-31
Hi,

thanks for your replies.  It does indeed seem gdm is the culprit. I had put the multiseat setup on hold for a while, but i might give it a go with a different *dm. Thank for the tip about groovix, i'll have a look into that.

As far as userful goes, i did try that but it tended to crash only minutes after login in a second user. I didnt feel like trying to find out what the problem was there.

Maybe i'll just have to wait for 8.04 or switch away from ubuntu alltogether.

Regards,

Silby

---

### Post by Silby on 2008-02-14
Downgrading GDM to 2.18 finally allowed me to setup a multiseat station the way it was described on netpatia. The Xephyr.sh script provided by that site does not work though, as the output from proc/bus/input/devices has slightly changed. However just changing the first grep line with -A2 to -A3 fixes that too.

Don't you just love it when updates break older functionality.

---

