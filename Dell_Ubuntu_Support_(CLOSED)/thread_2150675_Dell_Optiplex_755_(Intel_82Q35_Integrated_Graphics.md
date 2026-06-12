---
title: "Dell Optiplex 755 (Intel 82Q35 Integrated Graphics) Ubuntu 12.04 slow"
date: 2013-06-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bastones on 2013-06-01
Hi everyone,

I hope someone can help resolve this problem for me as I have tried searching about this without any luck. I have a Dell Optiplex 755 desktop and I decided to replace Windows Vista with Ubuntu 12.04 LTS. However, using 12.04 is extremely sluggish at times (the user interface) and application windows regularly stall and fade (freezing). I have seen [this bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/931122") which looks identical to the problem I am having.

Specifications: Intel® Core™2 Duo CPU E4700 @ 2.60GHz × 2 and 2 GB RAM.

Any help is appreciated, thank you.

---

### Post by PhilGil on 2013-06-01
@[**[COLOR=#000000]bastones[/COLOR]**]("http://ubuntuforums.org/member.php?u=558619"), what is your monitor resolution? Are you running a dual monitor setup?

---

### Post by bastones on 2013-06-01
> **PhilGil said:**
> @[**[COLOR=#000000]bastones[/COLOR]**]("http://ubuntuforums.org/member.php?u=558619"), what is your monitor resolution? Are you running a dual monitor setup?

Hi Phil,

Thanks for your response. 1920 x 1080, and I'm not running a dual-monitor set up.

Thanks,

Ben.

---

### Post by bastones on 2013-06-01
Just to update, I have upgraded from 12.04 LTS to 13.04 just to see whether it is any faster, and it does seem *a lot* faster using it in general. Although for some reason the Unity Dash and the new shutdown/restart "Are you sure?" dialogue overlays seem to have graphical artifacts ([see screenshot]("http://b3ns.com/images/forums/screenshots/UbuntuForums/unity.png"), and [this]("http://www.b3ns.com/images/forums/screenshots/UbuntuForums/unity-shutdown-restart-dialogue-overlays.png") displaying the artificats in the overlay shutdown dialogue and a [thread]("http://ubuntuforums.org/showthread.php?t=1782493") someone else has posted about the same problem).

---

### Post by PhilGil on 2013-06-01
Thank you, Ben. The reason I asked about your monitor setup is because the chipset has a maximum resolution when using hardware acceleration. I have two 755's and discovered the problem when I added a 2[SUP]nd[/SUP] monitor to my office machine – suddenly my desktop slowed to a crawl. It turned out the combined horizontal resolution of the two monitors (1280px + 1600px) was too large for the graphics to handle, and I had to switch to a non-composited XFCE setup.
 

 I'm sorry that this doesn't solve your problem. For what it's worth, I use Debian 7 and hardware acceleration in Gnome 3 works fine on my home machine (which has a single 1920x1080 monitor). As Wheezy and Ubuntu 12.04 package versions are roughly equivalent, I'd start looking at what's different – maybe Compiz would be a good place to start.
 

 Good luck.

---

### Post by bastones on 2013-06-02
Just to provide an update regarding the screen artifacts in the Dash and the Shutdown/Restart dialogues, [see this bug report]("https://bugs.launchpad.net/nux/+bug/1087534"). A workaround for this issue for now is to use the Unity Tweak Tool (found in the Ubuntu Software Centre). From the Unity Tweak Tool, go to Unity -> Search and disable the background blur.

---

