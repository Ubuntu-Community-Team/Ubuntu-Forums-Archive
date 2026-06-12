---
title: "Gnome resolution stuck at 640x480"
date: 2005-06-26
forum: Desktop Environments
---

### Post by richburr on 2005-06-26
I haven't ever been a big Debian fan, but we installed Ubuntu on a couple of boxes where I work and I liked it. I wanted to play with it more and did an install here at home, but the resolution in Gnome seems stuck at 640x480. When I go into the Gnome tool to change resolutions, it only shows that one on the list.

After some Googling I found the hint to try:

dpkg-reconfigure xserver-xorg

I did this and configured the server to only use 1024x768. I verified that the new configuration had been written to the xorg.conf (/etc/X11/xorg.conf IIRR), but when I rebooted I was still stuck in 640x480 like before. After that I edited the xorg.conf so that only this existed in the Screen section:

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
        Monitor         "CPD-200ES"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
EndSection

I rebooted and I was still in 640x480.

Any ideas? I've not run into this before...


Rich

---

### Post by xristos on 2005-06-26
Check the Section "Monitor" of xorg.conf and put the correct values of HorizSync and 
VertRefresh . You can look them up in your monitor's manual . Here is mine :

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	30-60
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

---

### Post by richburr on 2005-06-26
Thank you, that fixed it. I had to enter the values manually, though.

I tried running "dpkg-reconfigure xserver-xorg" again, and this time I chose the advanced option and entered the rates, but they still did not make it into the xorg.conf file. I had to edit the file and insert them into the Screen section, but once I did it worked.


Rich

---

