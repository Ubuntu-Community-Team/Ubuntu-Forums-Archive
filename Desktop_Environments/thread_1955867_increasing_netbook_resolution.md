---
title: "increasing netbook resolution"
date: 2012-04-10
forum: Desktop Environments
---

### Post by Miotas on 2012-04-10
Hi all, 


I'm trying to increase the max resolution of my netbook, an Asus Eeepc 1001px. The default is 1024x600 and I would like to increase this to 1024x768, to run a number of applications/games which prefer/require this resolution. 

On the default win7 starter, I was able to do this, but since moving to ubuntu 11.10 (and eventually lubuntu) I've lost this ability. 
(My only gripe - otherwise, lubuntu is perfect for this set-up!)

I've increased the resolution using jupiter but I the lower part of the screen is no longer accessible with my mouse. I also found some CLI commands which achieved the same thing (unfortunately, I cannot remember what this was, or find the information again...but I think it was with Xrandr, I've played around with Xrandr a lot!). I also tried editing xorg.conf, but like this person [here]("http://ubuntuforums.org/showthread.php?t=1137463"), I found that editing xorg.conf has no effect.

Has anyone with a netbook managed to display at 1024x768?
I'm just wondering what I'm missing here - I'm very new to Linux, so quite probably I'm missing something :) 

I'm also wondering if perhaps this is just some display bug with lubuntu/ubuntu? I was hoping upgrading to 12.04 might help, but no joy :(

Any insights are greatly appreciated, 


thanks

M.

---

### Post by solidsnake666 on 2012-04-10
When I installed ubuntu 11.10 I had to install drivers for my video card. In ubuntu I just had to launch additional drivers and that picked up the driver. Not sure if it's the same on lubuntu.

---

### Post by Miotas on 2012-04-10
There is no "additional drivers" facility. It seems you have to manually update. My netbook has onboard graphics - GMA3150. I've had a look at the intel site and they have some linux graphics drivers, I'm going to look into it a little more and see if its possible to upgrade and if that will help..

**edit: From what I've read so far - it seems that drivers are updated automatically through system updates?
Based on what I got from this:

sudo lshw -C video

My driver version is i915.

---

### Post by Herpythebrony on 2012-04-10
Try out xrandr. its a terminal based application for changing the resolution. I used it when I was running Fluxbox.

---

### Post by Miotas on 2012-04-11
I did try xrandr. I managed (after a lot of playing around) to change the resolution, but still had the issue where I could not access the lower 1/5th of the screen with my mouse...

Basically- visually it looked 1024 x 768, BUT the area accessible was still 1024 x 600.

I hope that's clearer.. ? 

Perhaps it makes sense that it is a driver issue?

Its really bizarre..

---

