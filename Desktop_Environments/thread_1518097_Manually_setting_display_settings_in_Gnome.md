---
title: "Manually setting display settings in Gnome"
date: 2010-06-26
forum: Desktop Environments
---

### Post by tacomanii on 2010-06-26
Ok, this might seem like a stupid issue, and I am not completely new to linux and gnome but I am not an expert. I installed ubuntu on a really old desktop computer that I have, which doesn't have the greatest video card, but it isn't terrible. I am using the computer hooked up to a 1080p television. 
 
When it loads up ubuntu, it automatically detects the settings and resets, but my tv says it can't display the video. I have an old CRT monitor I hook it up to to be able to change settings, but it won't let me change the settings in gnome for the TV. I think the settings it will need to have for the video card hooked up RGB and television would be 1336x768, is there a way that I can program that to where it doesn't automatically detect the monitor?
 
Sorry if it doesn't make sense, but so far I am enjoying unbuntu on my laptop computer.
 
Thanks in advance!

---

### Post by DaftPunker on 2010-06-26
What's your video card? If you don't remember, run "lspci | grep VGA" and post the output here.

Post your entire /etc/X11/xorg.conf too. Are you connecting the TV using a HDMI cable?

Which desktop resolution do you use in this computer when you connect a RGB monitor?

---

