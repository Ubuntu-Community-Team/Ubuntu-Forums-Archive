---
title: "Twinview Monitor Positions"
date: 2009-11-07
forum: Desktop Environments
---

### Post by mikegeig on 2009-11-07
Hello everyone, I currently have installed Ubuntu 9.10 with an nvidia 9800 GT graphics card installed. I am attempting to setup my twinview and am having some issues.

So far, I can enable both monitors and get twinview working great. The only problem is that my monitors are not side by side, instead one is mounted above the other. Whenever I change the positioning of the secondary monitor inside nvidia-settings, the screen gets all crazy and parts of it go black. The computer doesn't freeze up, but I can't see anything. Can anyone point me in the right direction?

EDIT: If this isn't in the right place, I apologize.

---

### Post by mikegeig on 2009-11-09
Bump, anyone?

---

### Post by Sigma47 on 2009-11-09
By all means Im no expert and haven't encountered this myself but, under the nvidia-settings GUI, "gksudo nvidia-settings", have you checked the advanced button and checked that your panning area can contain your resolutions. if you have for example DFP1=1052x768, DFP2=1052x768 you need a panning area of 2104x768 if your monitors are side by side...other than that I am useless. good luck

---

### Post by doas777 on 2009-11-09
ok. in nvidia-settings, right next to teh monitor resolutions, there shoudl be a text box called position (may be a dropdown). make sure that your secondary monitor says "Left" or "Right"

if you are looking at numbers (+0, +0) or (+1024, +0) then the position is in terms of offset. set the primary to "absolute" and the secondary to +<firstmonitorwidth>

---

### Post by mikegeig on 2009-11-10
> **doas777 said:**
> ok. in nvidia-settings, right next to teh monitor resolutions, there shoudl be a text box called position (may be a dropdown). make sure that your secondary monitor says "Left" or "Right"

if you are looking at numbers (+0, +0) or (+1024, +0) then the position is in terms of offset. set the primary to "absolute" and the secondary to +<firstmonitorwidth>

I don't want the monitors left or right. I can do that already. I want my secondary above my primary. As soon as I do that, it crashes.

Also, as far as panning goes, that just gives me the ability to pan my monitor. I don't believe it has any bearing on how to two interact.

---

### Post by doas777 on 2009-11-10
> **mikegeig said:**
> I don't want the monitors left or right. I can do that already. I want my secondary above my primary. As soon as I do that, it crashes.

Also, as far as panning goes, that just gives me the ability to pan my monitor. I don't believe it has any bearing on how to two interact.

in that case, your top monitor woudl be (+0, +76 ) assuming a 1024*768 res

also look at the server layout section of your xorg. you may be able to apply "above"/"below" for your screen positions.

---

### Post by mikegeig on 2009-11-10
> **doas777 said:**
> in that case, your top monitor woudl be (+0, +76 ) assuming a 1024*768 res

also look at the server layout section of your xorg. you may be able to apply "above"/"below" for your screen positions.

Yes, I have done that...and it crashes my x server.

My monitors are 1680x1050 and 1280x1024. Is it that my main is too big for this to work?

---

### Post by doas777 on 2009-11-10
> **mikegeig said:**
> Yes, I have done that...and it crashes my x server.

My monitors are 1680x1050 and 1280x1024. Is it that my main is too big for this to work?

you may have to resign yourself to seperate xscreens in that case

---

### Post by mikegeig on 2009-11-10
> **doas777 said:**
> you may have to resign yourself to seperate xscreens in that case

Seperate x screens works, but I would much prefer to figure out why this is happening and fix it. Is there another place I can go to get support?

---

### Post by doas777 on 2009-11-10
the nvforums are alright for nvidia. hopefully they will help. traditionally twinview required two screens of the same res, but now a days you can get away with at least minor differances (1024 and 720x480 for instance) but I don't know for ATI. crawl their site a bit, and hit google, is the best advice i can give you.

have you tried a driver directly from NV?

---

### Post by norwoods on 2009-11-10
i have a 1920x1200 and a 1600x1200; they work fine above, below, left or right on a 9600gt and ubuntu 9.04.

---

### Post by mikegeig on 2009-11-12
Did you do anything special to get that configuration to work? Which driver did you use?

---

### Post by norwoods on 2009-11-12
ubuntu 9.04 64 bit
NVIDIA Driver Version:190.42 from [http://ppa.launchpad.net/ubuntustudio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntustudio-dev/ppa/ubuntu)

configured it with nvidia-settings

---

### Post by mikegeig on 2009-11-12
> **norwoods said:**
> ubuntu 9.04 64 bit
NVIDIA Driver Version:190.42 from [http://ppa.launchpad.net/ubuntustudio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntustudio-dev/ppa/ubuntu)

configured it with nvidia-settings

I really appreciate the help, but I am new to linux and i'm not entirely certain what you linked me. I browsed around there, but am not sure what I am looking for.

I am using ubuntu 9.10 32-bit.

---

### Post by norwoods on 2009-11-13
apt and synaptic load programs from repositories.  launchpad has a number of repositories and that is one of them.  you need these other repositories for a number of reasons, in this case it is because the nvidia driver is proprietary and ubuntu does not have proprietary programs on their repositories.  try the following link for more info
[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)

---

### Post by mikegeig on 2009-11-14
well, I have installed the new driver, but still experience failure when going above aand below. How are yours setup? Are you using the absolute/above setting or absolute/relative? Which is your primary?

Thanks again

---

### Post by prkos on 2009-11-14
I use Clone to get them one over the other (Twin view). 

For TV I set it's default resolution, but then under Advanced I put panning to be larger than tv resolution. 

Have you tried something similar?

---

### Post by norwoods on 2009-11-14
the larger one is primary.  i normally use left of from the menu which it converts to absolute.  i just tried above and below to see if my software works ok.

---

### Post by mikegeig on 2009-11-16
I am making progress, but the stability is still iffy. I completely uninstalled all graphics drivers and then manually reinstalled the nvidia driver from their website. Now I can put my monitors above and below (but not absolute, or "centered above", which is fine) however the gnome panels are appearing on my secondary monitor even though I chose my large monitor as my primary in the settings. Any attempt to relocate the gnome panels to the large monitor results in the screen blacing out and freezing up like before. 

Any suggestions?

---

### Post by norwoods on 2009-11-17
9.10 has a new xorg i believe.  you may have found a bug in the new software.

---

### Post by subbareddy on 2010-12-28
hi   my computer in nvidia settings  right of and left of  position and resolution:1440*900 working in dual monitors  but when i changed above and below is not working  why if you have any solution for that pls reply to me

---

