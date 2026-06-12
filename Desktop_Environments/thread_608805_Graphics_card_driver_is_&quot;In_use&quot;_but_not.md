---
title: "Graphics card driver is &quot;In use&quot; but not &quot;enabled&quot;..."
date: 2007-11-10
forum: Desktop Environments
---

### Post by LostJot on 2007-11-10
Hello,

After a year of travelling I am back to charge head down into another Ubuntu adventure. I have lots of experience of messing everything up, reinstalling and never getting anything to work correctly.
My last version was Dapper, I've now dived into Gutsy and already I've buggered it all up.

Installation was smooth, and seeing everything functional and A-OK I naturally panicked and decided to ruin it. I decided to install the nvidia driver. Unfortunately, I didn't think at all hard (or check), and went for the glx instead of legacy. The card is a GeForce 420Go, so fairly old and not especially good. Inevitably, on restart, I got a black screen. Finding myself in very familiar territory, I went into recovery mode and changed xorg.conf back to the nv driver, without first backing it up. Whoops. 
Next time, it all loaded fine.
So I removed the glx, and installed the legacy driver this time, enabled it, and restarted. Awesome, it's all there. Then I decided to enable desktop effects, I got the "could not be enabled" message, and found this thread
[http://ubuntuforums.org/showthread.php?t=568681](http://ubuntuforums.org/showthread.php?t=568681)
Which was very helpful, and I thought I had solved the problem, just by reducing the required memory on nvidia cards in compiz. However, it didn't seem to solve it. I did not restart. On second thoughts, I wonder if restarting may have helped. 
I did recall reading someone's advice that maybe disabling and re-enabling the graphics card driver may help. When I went to restricted drivers, the green tick mark was there, and the check box was filled. I disabled it, and restarted.
When I went back, it was red and disabled. As expected. I ticked the box and restarted to enable it.
Problems appeared when I got back, I found that I had a green tick for "in use" but the check-box was not filled. So it was "in use" but somehow not "enabled". What does that mean?
Checking the box resulted in no useful effects in terms of enabling it. 
Turning on desktop effects gave me the "please restart once your driver is enabled" message. But this did nothing, it seemed like whatever I did could not enable it. 
I also enabled it via the command line, but I got a message saying that as I had modified by xorg.conf file the script could not proceed (I should have backed it up) automatically, and that I should manually go into xorg.conf and change the driver from "nv" to "nvidia". But I had already done this. So I changed it from nvidia to nv, restarted, then back to nvidia again, restarted, get the splash screen, very nice. But it seems still the driver is in use but not enabled, and again, clicking to enable results in nothing. 

I suppose an obvious question is, am I wasting my time? Will compiz fusion run at all on an old 32MB nvidia card? I suspect that if it will, it won't run great. But I was planning to try it out anyway. This card does not seem to be on the blacklisted hardware page.

I do wonder whether a combination of installing the wrong driver, manually fiddling with xorg without backing up, repeatedly disabling and enabling the drivers and generally acting like a brainless hoon have contributed to my current situation. Perhaps I should re-install, use the right driver from the start, make sure to back-up xorg.conf? Or will I just land in the same position again?

Cheers,
The Buffoon

---

### Post by vinnn on 2007-11-10
Personally I think you're pushing it trying to get Compiz Fusion going on a 32MB GPU.
Did you try Ubuntu's built-in Compiz first to see if that works? It runs fine on my laptop with just 64MB of video memory, although in the past when running Beryl or Compiz Fusion on the same laptop it would run but some plugins such as the skydome just didn't work.

BTW as Ubuntu 7.10 uses a 'Bulletproof X' configuration, you can just remove the xorg.conf file and X will reconfigure itself with a new xorg.conf file. Possibly in vesa mode but at least you can start from there.

---

### Post by LostJot on 2007-11-10
Hi, at the moment all I've been trying to enable is the default desktop effects, which I thought were compiz with a few fusion plugins on top.

---

### Post by LostJot on 2007-11-10
Have just found a possible problem, that is I was using the legacy 7xxx series, whereas Nvidias own list said that I should be using legacy 9xxx series. 

[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

> The 1.0-96xx driver supports the following set of GPUs:
NVIDIA chip name 	Device PCI ID
GeForce2 MX/MX 400 	0x0110
GeForce2 MX 100/200 	0x0111
GeForce2 Go 	0x0112
Quadro2 MXR/EX/Go 	0x0113
GeForce4 MX 460 	0x0170
GeForce4 MX 440 	0x0171
GeForce4 MX 420 	0x0172
GeForce4 MX 440-SE 	0x0173
GeForce4 440 Go 	0x0174
**_GeForce4 420 Go 	0x0175_**

However, the only one I could find at packages.ubuntu.com was the 7xxx series....
I have found the Legacy 96.43.01 at Nvidia, so I will try this out. 
(I am on a clean install now :D )

---

### Post by LostJot on 2007-11-10
Update:

May have found part of the problem.

Restricted drivers prompted me to install glx. This gave me the blank screen problem. I immediately assumed that I had screwed up and needed a legacy driver. It seems this was not the case, and that the blank screen issue is known with this card and the glx driver:
[http://ubuntuforums.org/showthread.php?t=417188](http://ubuntuforums.org/showthread.php?t=417188)

So the issues I had afterwards (not being able to apply effects, not being able to enable driver properly) were most likely because I was not supposed to be using the legacy driver. 
So the legacy driver fixed the blank screen, making me think it was the right thing to do, but it just covered up other problems. 
So I will try some of the fixes from the above thread.

---

### Post by LostJot on 2007-11-10
It's solved. 
Problem was, yes I should not have used Legacy. Everything then rolled from using the glx-new driver.
Fixed black screen problem. 
Then Compiz gave me the Windows sans Frontieres problem, fixed this with a quick edit of xorg.conf, now compiz is running fine, I haven't tried anything too excessive, but the cube and windows effects all work, along with fire writing, etc and no sign of the laptop struggling or getting hot. Yet.

---

