---
title: "How to run multiple X servers with Intel graphics?"
date: 2013-05-06
forum: Desktop Environments
---

### Post by PeterTaps on 2013-05-06
Folks,

I am running Ubuntu minimal plus openbox. 

Earlier, I was using nVidia card. The card supported HDMI output (for my projector) and a VGA output (for a monitor). Application nvidia-settings would let me run two x servers for two different displays. I would run VLC on the projector display (DISPLAY=0.1) and do other things on my monitor display while watching the movie. 

I now have a new box with a better motherboard that had on-board Intel graphics and I don't need nVidia card anymore. 

xrandr -q shows that I have a VGA output and a HDMI3 output.

I am able to use xrandr to set the resolutions for each of the displays. I am also able to place one display on the side of the other.

However, I would like to set it up such that I can  have two different x servers as before.

I don't have any xorg.conf file in /etc/X11 directory. As I understand, xorg.conf is no longer needed and that I should be able to use xrandr to achieve pretty much what I wish to achieve. However, I don't understand how I can set VGA display to one xscreen and HDMI3 display to another xscreen.

I would appreciate it if someone can help me understand how I can achieve this.

Thank you in advance for your help.

Regards,
Peter

---

