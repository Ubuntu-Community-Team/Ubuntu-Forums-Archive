---
title: "Black Screen Flicker in Ubuntu 11.04 / Gnome3?"
date: 2011-06-16
forum: Desktop Environments
---

### Post by CodyLoco on 2011-06-16
Hi guys- 
I'm getting the occasional full-screen black flicker on my laptop, it's an Asus G73JW with an nVidia 460M card, running the restricted drivers.  I've installed Gnome3, and so far like it more than Unity, but the flickering needs to stop :P

I'm just wondering if anyone has figured out a solution yet?  I've also noticed that some animations aren't as smooth as they should be, like when I hit the top-left corner to bring up the dock it studders just a wee bit...

Thanks!
Cody

---

### Post by CodyLoco on 2011-06-18
Hi?

---

### Post by CodyLoco on 2011-06-19
Bump?

---

### Post by maverick280857 on 2011-06-23
You're not alone. I have the same problem on my Dell XPS 15 (NVIDIA GT435M). Are you using the latest drivers from NVIDIA?

---

### Post by CodyLoco on 2011-06-23
> **maverick280857 said:**
> You're not alone. I have the same problem on my Dell XPS 15 (NVIDIA GT435M). Are you using the latest drivers from NVIDIA?

I'm not, I'm just using the drivers that auto install with the restricted drivers package.  I don't want to do anything that will make things worse because I have seen people complaining about entire windows or menus going black and staying that way.  Right now, it's more of just a (serious) annoyance but i can work with the computer.  If anything got semi permanently obscured I would have problems.

It's weird though that it only happens in normal programs.  When I boot up Eve Online or even just a video, I don't see any flickering.  I thought it would be the other way around...

---

### Post by rogue1987 on 2011-06-26
I've been seeing flicker as well, or rather I get a black flash every so often. I have an older HP Pavilion running nvidia 173 driver. but I've had lots of graphics problems since loading 11.04 on this laptop.

---

### Post by maverick280857 on 2011-07-03
I reinstalled Ubuntu 11.04 64-bit on my Dell XPS 15 just a couple of days back. I have **not** yet reinstalled Gnome 3, but I am experiencing VERY frequent and very irritating flicker. So I can tell you that it has something to do with the NVIDIA drivers but most probably nothing to do with the with Gnome 3.

---

### Post by CodyLoco on 2011-07-03
Well that sure sucks...... I sure wish I could find a fix because every time I switch to Ubuntu from windows, I eventually find something I can't fix and can't live with and eventually end back on Windows (which sucks!)...

This time it's this flickering thing, and really poor flash performance - artifacting and slow video FPS from flash...  I also can't get suspend to work....

:(

---

### Post by maverick280857 on 2011-07-03
Looks like its a power manager issue. I unchecked the dim brightness when idle (on battery) option, and the flicker seems to have gone...for now <fingers crossed!>.

See attached screenshot and also [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/155244](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/155244)

---

### Post by maverick280857 on 2011-07-03
Okay I am wrong. The flicker has reappeared. BUT it happened when I was on the nvidia website, so I am wondering if it is connected to Flash.

[http://danielj.se/2011/01/06/how-to-fix-flickering-flash-videos-in-firefox-4-in-ubuntu-64-bit/](http://danielj.se/2011/01/06/how-to-fix-flickering-flash-videos-in-firefox-4-in-ubuntu-64-bit/)

---

### Post by CodyLoco on 2011-07-03
> **maverick280857 said:**
> Okay I am wrong. The flicker has reappeared. BUT it happened when I was on the nvidia website, so I am wondering if it is connected to Flash.

[http://danielj.se/2011/01/06/how-to-fix-flickering-flash-videos-in-firefox-4-in-ubuntu-64-bit/](http://danielj.se/2011/01/06/how-to-fix-flickering-flash-videos-in-firefox-4-in-ubuntu-64-bit/)

Yeah I had disabled that too and it lowered the amount of flickering - and yes, flash seems to make it worse, but i do get ocassional flickering w/o flash loaded (ie, haven't viewed a site with flash)... so I think it's a combination of things. 

Whats weird tho is that if I load EVE Online, I get no flickering in game...  which you'd think should be the worst time for flickering...?

---

### Post by ondemanddesign on 2011-07-15
I am also having the same issue. This is annoying as hell. I have a desktop so I can't choose the power options.

---

