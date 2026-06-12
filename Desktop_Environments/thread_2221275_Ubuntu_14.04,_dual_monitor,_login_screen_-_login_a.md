---
title: "Ubuntu 14.04, dual monitor, login screen - login appears on &quot;wrong&quot; montor"
date: 2014-05-01
forum: Desktop Environments
---

### Post by pablosquared on 2014-05-01
New install of Trusty. I've configured the monitors such that the larger one, on the left of the overall display, is the primary - I use that one for most apps, except music and TV, which are set to appear on the smaller right hand monitor. All of that is ok.

However, when the system boots, the lightdm login appears on the RHS, secondary, monitor. This is slightly annying, and differs from every other installation I've done. How can I make the login dialogue appear on the primary monitor?

Yeah, I know. First world problems... ;)

---

### Post by smallming on 2014-05-01
i will like to know the solution to the problem too. oh yeah first world problems :redface:

---

### Post by ktulu77 on 2014-05-15
I have the same problem. The primary screen is set to HDMI-0. But my TV is turned off most of the time, so I cannot choose my session ...
I tried a workaround by adding a session-script :
sudo gedit /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
inside put
session-setup-script=/etc/lightdm/monitor1-off.sh
and in this script, I put a xrandr command :

#!/bin/bash
xrandr --output HDMI-0 --off --output DVI-I-3 --primary

But it does not work (my command works when launched from my session)

---

### Post by pablosquared on 2014-05-16
I found that moving the mouse to the right, "off screen", resulted in the login dialogue moving to the left hand monitor, where I want it. Like the screen wrapped round. Moving it to the left didn't work for me so the fix in my case was slightly weird and non-intuitive, but it works. 

Bit trickier to do if your secondary monitor is switched off, though.

---

### Post by lemonterror on 2015-03-31
I had this same problem and it has been bothering me for a while, but I finally found a fix. This is one of the top things that comes up in google, so I thought I would post the solution here.

The solution is here: [https://code.launchpad.net/~albertsmuktupavels/unity-greeter/add-primary-monitor-support/+merge/202627](https://code.launchpad.net/~albertsmuktupavels/unity-greeter/add-primary-monitor-support/+merge/202627)

But basically, ubuntu doesn't know which screen to use before you sign it. If you copy /home/[user]/.config/monitors.xml to /var/lib/lightdm/.config/ it should fix things, assuming you have things set up properly on your own profile.

---

