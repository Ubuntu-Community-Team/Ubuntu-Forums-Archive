---
title: "Pentium 4, Nvidia GeForce4 MX 420"
date: 2014-04-14
forum: Desktop Environments
---

### Post by dave0109 on 2014-04-14
I had the inevitable request to do something with an aging PC running XP, so I put Lubuntu on it (on a separate drive).  

However, there were some issues when displaying icons and highlighted text.  Running the file manager, some directories and files would come up with icons and some would not. Hovering the mouse over where the icon should be would sometimes show the icon for that item, but then an icon (or 2) might disappear for other items.  There didn't appear to be any consistency.

In addition, the highlighted text in the left hand pane of the file manager didn't have a background colour of the selected item and as the text is normally white, there was just a faint green "shadow" on the text, meaning it was difficult to read.  This seemed to happen on other dialogs as well - because I went to change the theme / window decorations to see if that would help and it didn't seem to.  At this stage I was running out of time, so didn't go into things too deeply.

As it was, I had to leave it and the PC is back to XP for now (yeah, I know).

I don't know what CPU spec this thing had, but it's a 12 year old Dell Dimension, with 1GB RAM.  I thought that would be enough to run Lubuntu, so am a bit perplexed by the display issues.

Any ideas?

---

### Post by sudodus on 2014-04-14
1 GB RAM is adequate for Lubuntu. But if you specify also

CPU
graphics chip/card
wifi chip/card

it will be easier to help. See also this link
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

### Post by dave0109 on 2014-04-14
Yeah, I'll have to ask about the Gfx card.  I think the CPU is a 2.66GHz Pentium 4.  No wifi card.

---

### Post by sudodus on 2014-04-14
2.66GHz Pentium 4 is OK

---

### Post by ajgreeny on 2014-04-14
Some old XP computers suffered with **sis** graphic cards which are not well supported by Linux at all.  You may get it to work,though it may be in low graphics mode or low resolution, but if that is the card in question it may have even more difficulties.

---

### Post by KBD47 on 2014-04-14
Also recently had an old Dell and the graphics were crap with Ubuntu. You have plenty of ram. I would try Debian or Linux Lite. Those both had good graphics on the old Dell I tried them on. It had a video card that hasn't been supported since Ubuntu 10.04.

---

### Post by mörgæs on 2014-04-14
The problem with SIS graphics is solved in 14.04:
[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

Dave, XP is unsupported and hence a security risk. Please post a detailed specification of your hardware - it's very likely that we will get Lubuntu to work.
[http://www.computerhope.com/jargon/m/msinfo32.htm](http://www.computerhope.com/jargon/m/msinfo32.htm)

---

### Post by ibjsb4 on 2014-04-14
Yes, Lubuntu should work fine.

I run lubuntu-core on a 12 year old Dell P4@1.7GHz and half a gig of ram.

---

### Post by KBD47 on 2014-04-14
Good news about Sis, I lost support after Ubuntu 11.10 on one of my computers because of that and had to switch to Debian, but found that Linux Lite now works on that computer, I'm guessing a newer kernel.
Had trouble with an old Dell using Nvidia and found Debian and Linux Lite worked on it, but not Ubuntu.

---

### Post by eric13 on 2014-04-14
> **dave0109 said:**
> Lubuntu on it (on a separate drive).  
However, there were some issues when displaying icons and highlighted text.  Running the file manager, some directories and files would come up with icons and some would not. Hovering the mouse over where the icon should be would sometimes show the icon for that item, but then an icon (or 2) might disappear for other items.  There didn't appear to be any consistency.
In addition, the highlighted text in the left hand pane of the file manager didn't have a background colour of the selected item and as the text is normally white, there was just a faint green "shadow" on the text, meaning it was difficult to read.  This seemed to happen on other dialogs as well - because I went to change the theme / window decorations to see if that would help and it didn't seem to.  At this stage I was running out of time, so didn't go into things too deeply.

Humm, the description of display errors looks similar to what I got with a Nvidia Geforce2MX : [http://ubuntuforums.org/showthread.php?t=2168979](http://ubuntuforums.org/showthread.php?t=2168979) which refer to the bug with Nouveau drivers: [https://bugs.freedesktop.org/show_bug.cgi?id=51477](https://bugs.freedesktop.org/show_bug.cgi?id=51477)
May affect all Geforce 2/3/4 cards. So I updated this topic.
If you have such a card, bad luck, you should stick with an older version of Lubuntu, e.g. LXLE or Zorin OS if you want LXDE. More details on mörgæs topic mentioned by sudodus
The rest of the config is more than fine and Lubuntu should run much smoother than Win XP*: with 1 GB of RAM, it would be more than comfortable. And with a P4, you have SSE2 support, so no brainer here (flash player crash without, bad for Athlon XP CPUs)
*: especially because you don't need these 100 AV/Anti malware SW which slow down your computer!!

---

### Post by KBD47 on 2014-04-14
I said Dell, but it was actually a HP with Nvidia card:
[COLOR=#000000][FONT=Proxima-Nova]GeForce4 MX440 

That one would only run on Linux Lite and Debian Wheezy without weird video artifacts. All the Buntus looked weird on it. Lite is based on Ubuntu but with a much newer kernel I think. Lots of these retiring XP machines are going to have old graphic cards. Will be great if the newer Ubuntu version 14.04 works well on these machines.[/FONT][/COLOR]

---

### Post by eric13 on 2014-04-15
as expected, your PC is affected by the bug I was mentioning just above. According to the bug tracking (see comment #23), it looks quite bad for Ubuntu 14.04: there is probably not much effort from the community to support these old graphic cards... I will not put too much hope there.

Do you run the default driver on Linux Lite and Debian[COLOR=#000000][FONT=Proxima-Nova][/FONT][/COLOR] Wheezy? It is the "nouveau" driver? 

Both are built on older Xorg server (1.11 and 1.12). They are the last supported by the nvidia proprietary drivers 96xx you could also try to get better 2D/3D performance. These are not supported in Ubtuntu 13.x and above, that is why it is better to sick with older distrib, like those based on Ubuntu 12.04 LTS (as your Linux Lite).

---

### Post by mörgæs on 2014-04-15
Please wait with this kind of statements until original poster tells which graphics card is in use.

---

### Post by dave0109 on 2014-04-15
OK, I've got hold of the proper specs for the PC.  It's actually got a Pentium 4 1.80GHz, and the Gfx Card is an NVIDIA GeForce4 MX 420 with 64MB

Thanks for all the replies so far.  I'll have a read about the Nouveau bug.

---

### Post by mörgæs on 2014-04-15
Well done, Eric. It was indeed one of the old Nvidias.
I agree that this card is a problem. Worth a try to see if you can get another used card for free or very cheap.

---

### Post by dave0109 on 2014-04-15
I can certainly try to source another card.
I wanted to stick with one of the buntus as it's something I'm familiar with and I'm going to end up having to support this PC. Still, I'll take a look at the others too.
Thanks for all the help.

---

### Post by eric13 on 2014-04-15
oops, I just see I mixed KBD47 and dave0109 in my former reply: I though KBD47's answer was from the original poster dave0109. Sorry. Since it applies to both, I suppose it's ok ;)
Anyway, KBD47, I am still curious to know which driver you are using with your GF4, if open source or proprietary.

---

### Post by KBD47 on 2014-04-15
I was weighing in on Dave's issue because it sounded very familiar.
Eric, yes, using the open source driver. I think I would need to go back to Ubuntu 10.04 to get the proprietary driver to load on that old machine. Debian Wheezy and Linux Lite work great with the open source Nouveau driver, but for some reason I get artifacts on all the 12.04 Ubuntus and newer, though I haven't tried 14.04 yet on that computer.
Edit: From your earlier post it looks like no hope for any future Buntus with that old Nvidia card. I'm very curious what Linux Lite does differently than the other Buntu 12.04s, because it even works on another old computer I have with a SIS card that the other 12.04s won't work correctly on. Maybe regular Ubuntu needs to get with those Linux Lite guys on this Nvidia issue :-)
Edit2: Actually Linux Lite is not using Nouveau on my machine. inxi -F says it's using fbdev.

---

### Post by eric13 on 2014-04-16
ok for Linux Lite with the Framebuffer.
But that Nouveau works great  on Wheezy (Xorg 1.12) but not on Buntu 12.04 (Xorg 1.11) or more recent  versions (Xorg 1.13+) is very strange. 
And also I don't understand why the proprietary driver will not load on 12.04 and Wheezy.

---

### Post by KBD47 on 2014-04-16
I tried the following on that old machine: Debian Wheezy, worked out of the box, loaded Nouveau. Then I tried Xubuntu 12.04-weird artifacts, Lubuntu 12.04-weird artifacts, Peppermint-looked better, but a few weird artifacts, then Linux Lite and it looked great. Debian is a bit more stripped down than Ubuntu, so I wonder if they changed something. Also, I loaded Ubuntu 10.04 and it looked great, and asked to install the Nvidia driver, but I have a wireless dongle on that machine that 10.04 wouldn't recognize. I'm curious if it would be possible to install 10.04 and then upgrade to 12.04 without losing that driver, but I have the machine the way I want it now and don't want to experiment with it at this point.

---

