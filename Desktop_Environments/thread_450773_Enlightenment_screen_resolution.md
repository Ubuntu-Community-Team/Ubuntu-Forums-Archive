---
title: "Enlightenment screen resolution"
date: 2007-05-21
forum: Desktop Environments
---

### Post by toylas on 2007-05-21
Hi all, 

I had posted this one in another [thread]("http://ubuntuforums.org/showthread.php?t=412108") but did not get any response. So here it is as a new post. This problem is driving me crazy. Help plzz
-----------------------------------------------------------------------------------------------------------------------------------
Hi all,

This is not exactly related to Ubuntu but is related to Enlightenment and X in general. I have a really old desktop on which I have installed Elive. The problem is that enlightenment does not seem to consider higher resolutions for the monitor. My xorg.cof has all the resolutions specified

################################################## ###################
.
.
.
Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc 3D Rage I/II 215GT [Mach64 GT]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
EndSection
.
.
.
################################################## #####################

But when I log into enlightenment, it comes up only in 800x600. When I try to change it from configuration panel, it gives me options only for 800x600 & 640x480. I've searched a lot over the net but the only things I could find were modifying the xorg.conf but that does not seem to work for me (maybe I'm missing something here). Any suggestions or pointers will be great help.

Thanks,
Tulasi

---

### Post by Kobalt on 2007-05-21
Try to remove in your xorg.conf all the resolutions you don't want. Save and close and finally restart X with Ctrl+Alt+Backspace.

---

### Post by toylas on 2007-05-21
Thanks for the suggestion kobalt but it did not work :( it almost seems like Enlightenment does not even recognize the xorg.conf. It came up with 800x600 even after removing the 800x600 & 640x480 resoultions from xorg.conf :(

---

### Post by Kobalt on 2007-05-22
Did you install the drivers for your ATI graphic card ?

---

### Post by siteguru on 2007-05-22
What if you do a Recovery Mode boot up and at the prompt enter the root password then do **dkpg-reconfigure xserver-xorg** and follow the prompts? (Being sure to enter the required vertical and horizontal frequency ranges, and selecting the required resolutions).

---

### Post by toylas on 2007-05-23
I did dpkg-reconfigure xserver-xorg but it still does not show me the resolution I want. The same monitor had nice resolution in windows XP so I suppose it is not a problem with hardware. After reconfiguring Xorg it shows a lot of display options (which are not there in xorg.conf :-/ ), all of them smaller than 800x600. some 7**x5** or even 320x240 (my cell phone had higher resolution than this :(). I'm going nuts with this thing. help plzzzzz

---

### Post by toylas on 2007-05-30
somebody give some ideas plz..............:( :( :( :(

---

### Post by phissure on 2008-03-23
I'm having the same problem, only the opposite.
I removed all the 1280x1024 resolutions from my xorg.conf, but enlightenment still runs at that resolution.
It's very hard to read... :)

---

