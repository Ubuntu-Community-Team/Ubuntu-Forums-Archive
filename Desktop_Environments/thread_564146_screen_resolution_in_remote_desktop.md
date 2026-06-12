---
title: "screen resolution in remote desktop"
date: 2007-09-30
forum: Desktop Environments
---

### Post by dguido on 2007-09-30
I have a headless gutsy box, configured to automatically log in as a specific user (with gdmsetup) and to start a vncserver (through Remote Desktop prefs). Whenever I connect with a VNC viewer, the screen is stuck at 800x600. I changed /etc/vnc.conf to use a geometry of 1024x768 and I also went into xorg.conf and removed every possible screen resolution except 1024x768. After rebooting the machine, my VNC window was still stuck at 800x600. I think this problem may be related to the box starting up headless.

How do I get my VNC server to automatically use a resolution of 1024x768 in my current setup?

Thanks.

---

### Post by dguido on 2007-10-01
I've done some reading and it seems that I'm not actually running VNC server which is why /etc/vnc.conf doesn't change anything. Because I set up remote desktop through the Gnome remote desktop prefs, I'm using Vino, which is basing it's settings off xorg.conf.

getting closer....

can anyone verify this?

---

### Post by isbent on 2008-06-11
Did you get anywhere with this?

I'm doing exactly the same thing, though I just left a user logged in after setup..

Though I have yet to test it;

The problem is that Xwindows will not allow resolutions out of the hardware's abilities. So it must be listed as a virtual resolution. 

Example:

       SubSection "Display"
               Depth   24
               Modes   "1024x768"     "800x600"       "640x480"
               Virtual 1280 1024
       EndSubSection



This information was regurgitated from [http://rclermont.blogspot.com/2007/09/video-resolutions-under-ubuntu-remote.html](http://rclermont.blogspot.com/2007/09/video-resolutions-under-ubuntu-remote.html)

Hope it helps.


Update:

This worked perfectly. I had to reboot and re login blind tho.
the easy way:
first, in your VNC session from Applications -> Accessories open a terminal,

sudo gedit /etc/X11/xorg.conf

which will open xorg.conf in a text editor

I added the display subsection inside the screen section, as the stock install left the display subsection out.

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
    SubSection     "Display"
        Depth       24
        Virtual     1024 768
        Virtual     1280 1024
	Virtual     1400 1050
    EndSubSection
EndSection


After a reboot and precarious logon, I had the stock display resolutions and a 1400x1050 virtual resolution. For some reason it left the 1280x1024 out. My native res client side is wide screen so that could have eliminated as a choice. But the 1400x1050 works perfectly. It can be a little sluggish, but it looks fantastic.

---

### Post by cyrusjunior on 2008-06-16
Hello Everyone,

I had a similar issue, so I went with this parameter to resolve the issue. Through the terminal I did rdesktop -g 90% x.x.x.x where the x is your ip address. This worked well as it fit my screen, but at the same time allowed me to work with my Ubuntu desktop. 

I hope it helps =).
CyrusJr

---

