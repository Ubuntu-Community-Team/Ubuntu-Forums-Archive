---
title: "Fonts, networking and wireless"
date: 2006-06-13
forum: Desktop Environments
---

### Post by kuad on 2006-06-13
I just installed Dapper over Breezy and things are looking good except for a few things that are bugging me. I don't really know much about Linux, but had Breezy slightly customised thanks to all the nice guides here. 

System: Asus W3N, 1.6GHz, 512Mb RAM, 60Gb HDD, ATI Mobility Radeon 9700

Anyway...

1. Terminal font (and conky)
The fonts are slightly squashed together / overlapping. How to rectify this? For both the terminal and conky, I have Bitstream Vera Sans Mono size 8. msttcorefonts are installed and subpixel smoothing is selected in font preferences. Everywhere else (Firefox, gedit, nautilus) the fonts look fine. Beyond that I don't know enough to think of a solution.
But if I change the font size to 10 everything looks ok. But I would prefer size 8 to save screen space.
Screenshots:
Current squashed fonts: [http://img126.imageshack.us/img126/1774/uglyfonts9oh.jpg](http://img126.imageshack.us/img126/1774/uglyfonts9oh.jpg)
Old nice conky font: [http://img159.imageshack.us/img159/327/oldconkynicefont8gq.jpg](http://img159.imageshack.us/img159/327/oldconkynicefont8gq.jpg)

2. Networking
I can only connect to the internet if the network cable is plugged in on boot. As I have laptop, this is very irritating since it won't be permanently connected to a (wired) network. After I make this post I'll test if I can still connect if I unplug, then plug back in.

3. Wireless
After every boot, the little blue "wireless" light on the laptop case is on even if the wireless connection (eth1) is not enabled in Networking. I'd rather switch off the wireless by default and turn it on/off myself when I want.

---

### Post by WorLord on 2006-06-13
> 1. Terminal font (and conky)

Try enabling autohinting for your font rendering.  From a command line:

sudo dpkg-reconfigure fontconfig

Enable Autohinting instead of Native, anser the other two questions as you like.  Restart X when done.

> 2. Networking I can only connect to the internet if the network cable is plugged in on boot.

Perhaps you should look into installing NetworkManager?

---

### Post by kuad on 2006-06-13
Thanks WorLord.

network-manager fixed problem 2.

But doing the fontconfig thing improved fonts slightly in the terminal and conky, but made them uglier in firefox and nautilus (and elsewhere, I presume - haven't checked). ie text looked slightly blockier and blurrier, especially bold text.

It's the horizontal spacing that is irritating me. Even when I did reconfigure fontconfig, the spacing improved slightly but not to the extent as in the second screenshot in my original post.

Any other ideas anyone?

---

### Post by kuad on 2006-06-14
Well if anyone is listening, I tried zenwhen's solution: [http://www.ubuntuforums.org/showthread.php?t=4456](http://www.ubuntuforums.org/showthread.php?t=4456) but the result is the same as dpkg-reconfigure fontconfig. I assume that the provided .fonts.conf would be the output of reconfiguring fontconfig.

---

### Post by WorLord on 2006-06-14
Experiment with the System -> Preferences -> Fonts dialog.  I'm using "best shapes" and I no longer have the horizontal spacing issues.

---

### Post by kuad on 2006-06-14
[QUOTE=WorLord]Experiment with the System -> Preferences -> Fonts dialog.  I'm using "best shapes" and I no longer have the horizontal spacing issues.[/QUOTE]
This was the first thing I tried, which unfortunately didn't fix the horizontal spacing.

---

