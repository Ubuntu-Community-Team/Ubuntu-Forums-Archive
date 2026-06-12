---
title: "Install issue regarding display resolution on both 12.04 and 12.10"
date: 2013-03-04
forum: Desktop Environments
---

### Post by rtedbyers on 2013-03-04
I just repaired a desktop machine by ripping out the hard drives that had failed and replacing them with a single SSD.  Obviously this drive had nothing on it.

I first tried to install from the 12.10 desktop ISO, and all went well until I told it to reboot at the end of the install (as I was directed to do by the installer).

Once it rebooted, the display was completely distorted, squished to the left half of the screen (which supports up to 1280x1024, as does the generic video hardware built into the motherboard - NB: I have no info on what brand the video is as that is not documented, so to get further info on that I'd have to rip open the case and try to find the video chips and see what info they have on them, and I ain't a hardware guy so that would be a big challenge).  But the mouse seemed to work as if the display was working properly.

When I checked the system settings for the display, it was stuck on 'Laptop', with a resolution of 800x600, and no matter what I did, it refused to let me change that, or even manually set it to the correct screen resolution.  This was so bad that the GUI was totally useless!

So, since that was a new install, I blew it away and tried the 12.04 desktop, and at least that result the GUI could be used.  However, the screen resolution is still wrong, stuck as 800x600, and it too refuses to let me change that!  As a result, while applications like MySQL Workbench work, the right half of the window it creates extended past the right edge of the screen.  

It seem absurd that the installer would, in both versions, regard this machine as a desktop (it is a rather heavy full tower - and is a basic generic clone with relatively decent components - it is a very fast machine).  

As I spent several hours configuring this, and installing a variety of packages I intend to use on it, I don't really want to blow away the current install.  Thus, I require a fix that will let me correct the display settings.  NB: This machine accesses a keyboard, mouse and screen through a KVM from Cisco, and as the other machines that access these devices all work fine, the issue is with the Ubtuntu desktop installation and configuration.  After this issue struck, I checked the reviews of Ubtuntu 12.10, and it seems that compared to 12.04, 12.10 leaves everything to be desired; so lesson learned,* 'wait until a new release starts getting good reviews before wasting time on it - it is not good to be on the bleeding edge of technological advance, lest you like to be the one bleeding.'*

So, I would appreciate any guidance on how to fix this without breaking anything else.

Cheers

Ted

---

### Post by Cheesemill on 2013-03-04
Can you tell us what graphics hardware the machine has please. You can find out by running the following command in a terminal...
```
lspci | grep VGA
```

---

### Post by rtedbyers on 2013-03-04
you're a genius, my friend!  ;-)

The result of that is: "VGA compatible controller: XGI Technology Inc. (extreme Graphics Innovation) Z7/Z9 (XG20 core)"

I guess I should say, I am a programmeer, not a system administrator.

Thanks.  Liv and learn, and I learned something from you.  Now, what is the fix?

Thanks

Ted

---

### Post by Cheesemill on 2013-03-04
[https://sites.google.com/site/easylinuxtipsproject/xgiz7z9](https://sites.google.com/site/easylinuxtipsproject/xgiz7z9)

---

### Post by rtedbyers on 2013-03-04
I followed the instructions provided on that page to the letter, but it changed nothing.  Any thoughts on why?

Thanks

Ted

---

### Post by JLeon85 on 2013-03-04
I had the exact same problem with an Nvidia card. I went into "software sources" under settings, and saw that it had automatically detected it and was listing several proprietary drivers. I just tried each of them until one worked. Perhaps not the most tech savvy solution, but it did the job. 

Also, with the 12.10 problems, I'm not sure if you tried this but booting under "nomodeset" through F6 in the initial live CD menu is one way to temporarily eliminate graphical problems until you can find a permanent fix.

---

### Post by Cheesemill on 2013-03-04
> **JLeon85 said:**
> I had the exact same problem with an Nvidia card. I went into "software sources" under settings, and saw that it had automatically detected it and was listing several proprietary drivers. I just tried each of them until one worked. Perhaps not the most tech savvy solution, but it did the job. 

Also, with the 12.10 problems, I'm not sure if you tried this but booting under "nomodeset" through F6 in the initial live CD menu is one way to temporarily eliminate graphical problems until you can find a permanent fix.

That isn't going to work for the OP, proprietary drivers are only  available for ATI and Nvidia cards, not for XGI cards like in this situation.

---

### Post by Cheesemill on 2013-03-04
SIS (which became XGI) are notorious for having poor Linux support for their graphics chips.

A quick google for 'z7/z9 ubuntu' brings up some more suggestions, I suggest you try your luck with whatever information you can find.
The easiest solution would be to pick up a cheap second-hand supported graphics card.

---

### Post by rtedbyers on 2013-03-04
Thanks

Under system settings, I did not see anything called software sources.  Does that mean the install is broken more seriously than I thought?

Anyway, in the Ubuntu Software Centre, I entered XGI, and found two entries called "X.Org X server - Sis display driver, one of which, xserver-xorg-video-sis, is installed, and the other, xserver-xorg-video-sis-Its-quantal, is not.  Both say that they provide the driver for all SiS and XGI Volari cards, and that they are built from the X.org xf86-video-sis driver module.  It must have identified the video as XGI, but that doesn't explain the settings it decided to use.

Thanks

Ted

---

### Post by rtedbyers on 2013-03-04
> **Cheesemill said:**
> SIS (which became XGI) are notorious for having poor Linux support for their graphics chips.

A quick google for 'z7/z9 ubuntu' brings up some more suggestions, I suggest you try your luck with whatever information you can find.
The easiest solution would be to pick up a cheap second-hand supported graphics card.
I had done a search using Google, but the signal to noise ratio was quite bad.

I do, though, have a partial fix.

If it would be helpful, I can post some info about error messages I got during intermediate steps that led to the configuration info below.

I used "cvt 1280 1024 60" to get the parameters I'd added to the xorg.conf I constructed following the instructions on that page to which you providded a link earlier.  I found, the hard way, that to get a proper display (version 12.04 - I am not about to give 12.10 a try any time soon), a monitor section as follows:

Section "Monitor"[INDENT]Identifier "Monitor-KVM"
   Modeline "1280x1024_60.0" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync
   HorizSync 45-65
   VertRefresh 60
   Option "PreferredMode" "1280x1024_60.0"
[/INDENT]
 EndSection

And changed the 'Monitor" line in the Section 'Screen" to use that.

There are two results worth reporting.  First, I now get the proper resolution, and now none of the apps I open extend their windows past the right edge of the screen.  That is good.  The not so good result is that each time I boot, now, I get a popup window with waht looks like an error message, with the following content:[INDENT]
Could not apply the stored configuration for monitors

none of the selected modes were compatible with the possible modes
trying modes for CRTC 310

CRTC 310: trying mode 1280x1024@60Hz with output at 800x600@60Hzz (pass 0)
CRTC 310: trying mode 1152x864@60Hz with output at 800x600@60Hzz (pass 0)
CRTC 310: trying mode 1024x768@60Hz with output at 800x600@60Hzz (pass 0)
CRTC 310: trying mode 1280x960@60Hz with output at 800x600@60Hzz (pass 0)
CRTC 310: trying mode 1280x854@60Hz with output at 800x600@60Hzz (pass 0)
CRTC 310: trying mode 1280x800@60Hz with output at 800x600@60Hzz (pass 0)
CRTC 310: trying mode 1280x768@60Hz with output at 800x600@60Hzz (pass 0)
CRTC 310: trying mode 1280x720@60Hz with output at 800x600@60Hzz (pass 0)
CRTC 310: trying mode 1024x576@60Hz with output at 800x600@60Hzz (pass 0)
CRTC 310: trying mode 512x384@60Hz with output at 800x600@60Hzz (pass 0)

CRTC 310: trying mode 1280x1024@60Hz with output at 800x600@60Hzz (pass 1)
CRTC 310: trying mode 1152x864@60Hz with output at 800x600@60Hzz (pass 1)
CRTC 310: trying mode 1024x768@60Hz with output at 800x600@60Hzz (pass 1)
CRTC 310: trying mode 1280x960@60Hz with output at 800x600@60Hzz (pass 1)
CRTC 310: trying mode 1280x854@60Hz with output at 800x600@60Hzz (pass 1)
CRTC 310: trying mode 1280x800@60Hz with output at 800x600@60Hzz (pass 1)
CRTC 310: trying mode 1280x768@60Hz with output at 800x600@60Hzz (pass 1)
CRTC 310: trying mode 1280x720@60Hz with output at 800x600@60Hzz (pass 1)
CRTC 310: trying mode 1024x576@60Hz with output at 800x600@60Hzz (pass 1)
CRTC 310: trying mode 512x384@60Hz with output at 800x600@60Hzz (pass 1)

[/INDENT]
I have no idea where the "CRTC 310" came from, or why it insists on output at 800x600 when that has no relationship to what the hardware (video chipset or monitor) can handle (and in system settings, it still insists that the machine is a laptop, with the improvement that I now get a selection of resolutiions from which I can choose - and the default is now 1280x1024).  I also do not know what all those numbers refer to that were returned by CVT.  What is 109.00?  And if the following numbers are one dimension of the screen resolution, then those higher than 120 are wrong as the monitor is old and doesn't go that high.  And what do -hsync and +vsync mean, and should they be there if HorizSync and VertRefresh are specified?

Is the popup window at boot really an error message, and if so, how do I fix it?  And if not, what would I do to suppress it?  Or is it something I can safely dismiss and forget?

Thanks

Ted

---

### Post by ManamiVixen on 2013-03-04
There is ZERO support for SIS/XGI. Have to get a replacement card.

---

