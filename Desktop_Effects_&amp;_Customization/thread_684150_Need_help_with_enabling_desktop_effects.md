---
title: "Need help with enabling desktop effects"
date: 2008-01-31
forum: Desktop Effects &amp; Customization
---

### Post by Djalmahal on 2008-01-31
Ubuntu 7.10
Compiz fusion
Intel 945 Graphic Card with Intel - Experimental modestting driver

2 days ago my system was fine, Compiz worked and everything, so I know that it can work.

Then I tried to install a graphic card driver that should work better (i810 driver so that no blue fields anymore appear when effects are applied to certain windows, etc), which resulted in a blank screen after re-booting. After going back to the original driver (Intel - Experimental modestting driver which worked before) I am now unable to enable "custom" effects in System>Preferences>Appearance>Visual Effects. Whenever I try to set it to anything but "none" I get the message "Desktop effects can not be enabled".

I read a lot of threads on this Forum, but none helped, i tried out a whole lot, like
 - reinstalling Compiz, Emerald etc
 - change session to xclient script during login (recommended by somebody to me earlier)
 - trying it without and with xserver-xgl
 - run "sudo dpkg-reconfigure xserver-xorg" to try different setting

I admit I don't understand the effect of these commands, but the have been suggested to me in my earlier post or the situation of the person they were suggested to seemed reasonably close to mine to give it a try.

So, here I am  after a lot of time spent to set my system back to where it once was. I am sure that if I can just enable the "custom" Visual effects it all will runs nicely

Here some print out:

When I run compiz

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

Tell me if you need more information

Thanks
Andreas

---

