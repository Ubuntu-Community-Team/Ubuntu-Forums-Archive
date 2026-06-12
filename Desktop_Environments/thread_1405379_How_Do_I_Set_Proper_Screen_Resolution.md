---
title: "How Do I Set Proper Screen Resolution?"
date: 2010-02-12
forum: Desktop Environments
---

### Post by wbee on 2010-02-12
Hello,

System>Preferences>Display tells me my screen is "unknown".

When I click "detect monitors" it does nothing.

The screen resolution is set incorrectly at 800X600, which makes pages' sides beyond the edges of the screen. 800X600 is the top setting on the drop down menu provided. Those,of course,are 4 to 3 ratios.

I looked up my monitor. It's LCD, WXGA+,17",with a maximum resolution of 1440X900,which is a 16 to 10 ratio.

I installed the nvidia proprietary monitor and it loaded it at 640X480,which is even worse,in addition to also being 4 to 3.

How do I reset my screen resolution to the correct value and keep it there?

Can I experiment plugging different resolution values into the proper shell code once I have it?

------------

Thank you

---

### Post by efflandt on 2010-02-13
First see what resolutions X can determine from EDID in /var/log/Xorg.0.log.  Usually a digital connection (DVI or HDMI) would automatically pick an optimum resolution, but VGA can be more temperamental.  Or amount of video RAM may limit resolutions depending upon color depth (bits per pixel) since some video RAM is used by X for fonts.

See [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) for testing modes, or once you find a modeline that is close, xvidtune may help fine tune that.  But not sure how nVidia proprietary drivers play into that or if there is an nVidia app for setting additional modes.

Some other posts have mentioned a method of downloading an EDID file and tying that into X if it cannot gather proper modes from the monitor itself.

For example if I connect a 1080p monitor to my desktop with DVI to HDMI cable, it automatically works at 1080p.  But when I connected my VGA laptop to same display, I could not even find a proper 1080p modeline from the laptop itself (image was horizontally scrunched and offset).  But I got a proper modeline from Xorg.0.log of my digitally connected desktop that worked great.  For an older laptop without enough video RAM to do 1080p, I was able to find a 1360x768 VGA mode that worked, even though that mode does not even show up on the digitally connected desktop (which just shows 4:3 modes and 720p/1080p).

---

### Post by Steam. on 2010-02-13
I posted a topic before here, the 2nd/3rd post in there is a solution.

[Here.]("http://ubuntuforums.org/showthread.php?t=1312435")

Once you set your resolution when you run gksudo nvidia-settings , be sure to save to X configuration file.

---

### Post by wbee on 2010-02-13
Thank you for the responses.

The second time I tried to boot up,after installing the nvidia proprietary drivers,the monitor showed a screen saying that the signal was out of range.

So,I reinstalled the operating system,and am not using nvidia,so when I tried the stuff on the posts to which you refer,I got "command not found" all the time.

I have on board nvidia geoforce 6100 and the terminal recognizes it.

What should I try now?

-----------

Thank you.

---

### Post by jamesmcginnis on 2010-02-15
Help?
I've managed to dual boot Windows 7 & Ubuntu
I have a 32" widescreen monitor (Bush TV) connected via a HDMI cable.
I had to reset the resolution in Windows from 1280 x 720 to 1176 x 664 50htz 32bit to get the screen to display correctly.

I've enabled the Nvidia restricted drivers in Ubuntu but it won't let me change the resolution to 1176 x 664

I quite a noob to Ubuntu and would appreciate any help anyone can give me to get the correct resolution.

---

### Post by Grenage on 2010-02-15
Try creating a custom xorg.conf, it's a lot easier when you have EDID issues.  I have a rough guide [here]("http://www.grenage.com/xorg.html").

---

### Post by wbee on 2010-02-15
Thank you,Steam.

Others,he's right. Try the link to which he refers for a discussion and solution.

---

### Post by aleenkhan on 2010-02-20
**How Do I Set Proper Screen Resolution?** 			
 			 			 		   		 		 		Hello,

Even I have faced the same problem . It been a month I installed a Dual Boot with Win XP & Ubuntu 9.10 Karmic Koala. 

Its all worked fine  but when I tried to set the screen resolution through

System>Preferences>Display tells me my Monitor is "unknown".

When I click "detect monitors" it does nothing.

The screen resolution is set incorrectly at 800X600, which makes page's sides beyond the edges of the screen. It shows 600x400 & 800X600 and 800x600 is the top setting on the drop down menu provided. Those, of course are 4 to 3 ratios.

My monitor is LG 700E 17" CRT & When I checked my computer's Display Adapter , I found it as Intel 82945G Xpress Chipset Family with a maximum resolution of 1280x1024. 

How can I install a suitable display driver for this? How do I set my screen resolution to my desire i.e., more than 800x600?

Would someone please help me for it?


Thank you

---

