---
title: "Saitek x45 joystick and throttle and Flightgear"
date: 2005-04-23
forum: Gaming &amp; Leisure
---

### Post by sedge on 2005-04-23
Hi
I would like to use my Saitek X45 joystick and Flightgear with K/Ubuntu.
I have the following problem Kubuntu and Ubuntu recognise the joystick but calibration will not work.
Any suggestion?
Thanks
Sedge

---

### Post by zamnedix on 2005-04-24
linux was not made for games like that, :roll:   get windows for games!  :grin: 
i hate microsoft, yet i have to use windows when i want to play games

---

### Post by Doctor Nick on 2005-04-24
[QUOTE=zamnedix]linux was not made for games like that, :roll:   get windows for games!  :grin: 
i hate microsoft, yet i have to use windows when i want to play games[/QUOTE]

Yeah, it was pretty ridiculous for him to expect help from a forum for UBUNTU GAMING SUPPORT [img]http://forumimages.somethingawful.com/images/smilies/emot-ssj.gif[/img]



PS: I've been wondering about X45 support in ubuntu as well.

---

### Post by DeadPlanet on 2006-06-15
Hi,
I'm new to Ubuntu, (about a week), but am a serious nerd, and am diving in deep to find things to waste time with.  I found Flightgear, and love it.
Given:  Your joystick will jscalibrate but not in flightgear?  Maybe your buttons work, but no the axis?  I have this problem with my ms sidewinder (gameport).
I found a bug report (google) that talks about an issue with jscalibrate, that it takes over the driver module.  The bug report had a solution, but said it wouln't work for gameport, only usb.  It actually works for gameport.
Solution:  After you jscalibrate, while the machine is running, and all is fine, unplug the joystick and plug it back in.  It worked for me.  
The module has to "regrab" the hardware?  before it can read it, otherwise the analog functions are trapped somewhere else.  
I also found that for games such as gl-117 (cool freebee) running it under sudo make it work for that game.  That did not work for flightgear, only unplugging and plugging did that.
I hope this helps you.
I have seen this problem in several other posts, so I will copy this message to them in hopes that some will find it useful.
Ken

---

