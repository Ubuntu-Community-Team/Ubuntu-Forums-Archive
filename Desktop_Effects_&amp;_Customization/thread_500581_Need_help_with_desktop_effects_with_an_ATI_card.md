---
title: "Need help with desktop effects with an ATI card"
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by jhargis1012 on 2007-07-14
Hi guys. First off, I am a complete Ubuntu/Linux noob. Please bear with my lack of knowledge, especially when it comes to the terminal.

Okay, here's what happening. FYI, I am using an ATI X1150 integrated graphics card, have an AMD Turion 64 X2 and 2 gigs of RAM. Not sure how much of this info you need, but I thought I'd give it anyway.

First, I installed Ubuntu. Everything worked well except the desktop effects. I click on desktop effects, and when I try to turn them on, I get a white screen.

Now, I did some research on this and attempted a fix (which probably just dug me deeper). Here's the link I was following:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

So anyway, I rebooted, and then it said something about me using a restricted driver. I clicked on the little icon up in the tray, and told it to enable the ATI driver I had apparently installed through the terminal. I rebooted again.

Now every time I try to click desktop effects I get an error "The Composite Extension is not Available".

What did I do wrong, and how do I fix this? I'd really like to get the desktop effects working, and now I'm afraid I've messed up the drivers for my gfx card. Help please!

---

### Post by silviasichigo on 2007-07-14
I am having a similar problem as well (as I am on my second bean) I did the patch in the link above and my ATI driver is working but I ran GLXGEARS and I can not get above 720 FPS when this machine was vista it was running Diablo II with no problems hours on end but if there is a solution to boost the graphics or get a driver crack that will allow full usage of the Card that would be great.
Thanks for any help this is a huge forum and searching is good if you know what you are looking for. I hope this is not considered a thread jack but more of a me too. :)

---

### Post by haden9 on 2007-07-14
Go to Terminal and do a:

$ fglrxinfo


The information displayed afterwards should be this (I have an ATI X1400 by the way so your result will vary).

***@*********-****:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6474 (8.38.6)

Also try following this website for installing your drivers:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C)

And for Beryl try this one:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL#Graphic_Card_Drivers_and_3D_Video_Acceleration](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL#Graphic_Card_Drivers_and_3D_Video_Acceleration)

Good luck!

:popcorn:

---

### Post by jhargis1012 on 2007-07-14
Unfortunately, none of those links helped me. I cannot understand it! When I type

sudo fglrxinfo

I can the following:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)

Again, my card is specifically an X1150 (which is still Xpress, I believe, but I don't know why it doesn't recognize my precise model).

I've tried everything I can find, and I'm still getting "The Composite Extension is not available".

Any help?

---

### Post by jhargis1012 on 2007-07-14
Okay, so I've used this link

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C)

to revert to the xorg driver (I think that's what I did) because I was realizing that I'd never disabled composite extension. I thought this might be a good thing to look into simply because of the particular error message I have been getting ("The Composite Extension is not available"). So then, once I was finished getting the xorg driver back, I was brought to a blue interface (I'm assuming it was the one for xorg), and it was asking me for information regarding my video card. I entered any information I knew, and skipped past the rest. However, the menus kept coming with more and more options, so I eventually just exited the terminal altogether.

I'm pretty lost right now. Suggestions?

---

### Post by jhargis1012 on 2007-07-14
Oh, and my gfx card is actually a Radeon Xpress 1150m.

---

### Post by penguinsoup on 2007-07-18
The ATI Radeon Xpress 1150M does not support Indirect Rendering using the xorg driver or the proprietary one from ATI.com, so no AIGLX.

You must use XGL!

I have the same card, and I am working on it now...

I just can't get the kernel to recognize the new module using the FGLRX driver from ATI.com

Works great in openSUSE...  Easier to compile & install.

Here is what I am working with now...

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by jimminy_kriket on 2007-07-18
jhargis were you using aiglx? no go with ati.

Try using envy to install your driver.

---

### Post by spmcd on 2007-07-19
I have the same white screen problem with an ATI Radeon Mobility 7500 card.  Yes, I know it is an old card, which is why I cannot seem to find a good source for installation help like the above link for 9500 -> cards. 

I am a newbie to Ubuntu and installed Feisty Fawn, anyone have suggestions?

---

