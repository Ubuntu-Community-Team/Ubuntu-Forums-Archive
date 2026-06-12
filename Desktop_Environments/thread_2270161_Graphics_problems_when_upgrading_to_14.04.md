---
title: "Graphics problems when upgrading to 14.04"
date: 2015-03-20
forum: Desktop Environments
---

### Post by vitaoma on 2015-03-20
Hello people,

I've been using Ubuntu flavours for the last ~2 years. I started with Ubuntu 12.04, then changed to Lubuntu 12.04, which helped a lot with performance. Then I had to upgrade to Lubuntu 14.04 because some package updates were no longer available for 12.04; after the installation, I wasn't able to use the OS because, upon logging in, the screen would go all white scrambled crazy (see pics). I thought this was a problem with Lubuntu, and changed to Bodhi Linux (then based on Ubuntu 12.04). I still have this Bodhi Linux running, but I'd like to change my OS to Lubuntu 14.04 or Bodhi 3.0, but I keep getting this same problem... so I thought, right, distros based on 14.04 are not compatible with my hardware. But then I tried installing Porteus OS and had the same problem, so I thought maybe I was getting some setting wrong, and would be able to use these OSs by changing it.

What could this be?

Thank you very much, and sorry for the low quality of the images.

---

### Post by grahammechanical on 2015-03-20
How does the live session run? If the live session runs fine but the installed OS has a problem like this then it could be due to the video driver.

The live session uses an open source video. I cannot speak for other distributions but when we install Ubuntu we get an option to install third party software at the same time. If we tick that box we will get a proprietary video driver. If on re-starting we get this problems then it could be the proprietary video driver and we may need to install without ticking that box. It is just a thought.

If the live session has this problem then we might need to add nomodeset as a boot parameter to the live session loading process. See this wiki page. Look for Changing the CD's Default Boot Options Section 6 -F6

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

By the way, I am of the opinion that when upgrading to a newer version of the OS it is best if we are running the open source video driver because the upgrade will bring in newer proprietary video drivers and that may cause problems, especially with older hardware.

Regards.

---

### Post by vitaoma on 2015-03-20
The live session has these same graphics problems, for both Bodhi 3.0 and Lubuntu 14.04... however, I remember among all those trials, there have been times when I could run the live session, but installation didn't work (which was really a great frustration).

---

### Post by vitaoma on 2015-03-20
I will try and see if Lubuntu (or Bodhi) has this nomodeset configuration.

---

### Post by vitaoma on 2015-03-20
Apparently, my current video driver is Nouveau, and all is running ok.

---

### Post by vitaoma on 2015-03-20
All right, so I tried the "safe graphics" mode for Bodhi 3.0, and the live ran ok (however with poor graphics). But then, after the installation, in what should be the login screen, there was nothing but a black screen and the mouse cursor... the problem persists.

For Lubuntu 14.10, I couldn't find no version with "safe graphics", -nomodeset or something alike.

---

### Post by vitaoma on 2015-03-22
So... any ideas of what I could do? I'm still in Bodhi 2.4 for the while...

---

