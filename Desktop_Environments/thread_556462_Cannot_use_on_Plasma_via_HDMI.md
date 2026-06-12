---
title: "Cannot use on Plasma via HDMI"
date: 2007-09-21
forum: Desktop Environments
---

### Post by Mutha on 2007-09-21
Hi,

First time on the forum and new to Unbuntu

I was hoping to move away from windows with my media centre but I cannot get 7.04 to work with my 42" Pioneer plasma TV.

I tried setting it up on the Plasma I got the screen asking what I wanted to do etc but it just failed at the start of the setup after the splash screen. I then set it up on a normal LCD monitor then once it was done plugged it back into the Plasma. I get a FATAL ERROR NO SCREENS FOUND message.

It is running throuh my Onkyo 605 AV amplifier via HDMI and i have no problems running Vist or Xp this way.

Is there some sort of config file that I will need to amend to get it going.

Any help would be appreciated as I really want to use Unbuntu.

Thanks

M.

---

### Post by g8m on 2007-09-21
I have a similar situation with a 42'' lcd tv. 
Only thing I changed was adding a "1920x1080" mode to /etc/X11/xorg.conf.
Another important parameter in xorg.conf are the settings for horizontal and vertical refresh rates.
I am afraid that you will have to tinker a litte in these script with an editor, so making a backup and doing some trial and error cant be avoided, me thinks.

---

### Post by musta78 on 2008-07-20
Same problem here.   Have tried to fix this in endless hours, but can't find a solution.

I have a LG 50PG6000 plasma.  The Nvidia settings detects the tv, but no picture.

If someone could post their working xorg file, it would be great.

The LG manual even has what all frequency posted at the diferent resolutions but nothing happens.

Anyone??

---

