---
title: "Low-res login screen with intel graphics driver (vesa driver works, but shows static)"
date: 2008-03-07
forum: Desktop Environments
---

### Post by pmorch on 2008-03-07
Hi,

I have an intel graphics card: > lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
So, naturally I used the "intel" graphics driver.

I'm experiencing two things:
[LIST=1]
[*]The GDM login screen is running at a lower resolution than 1600x1200
[*]There are no virtual terminals (CTRL-ALT-F1-6) (This is due to [a known bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/182865") with the intel driver)
[/LIST]

And this is the GDM login screen where I enter my username/password and not the splash screen, whose resolution is controlled in /etc/usplash.conf with supsequent update-grub.

Several postings suggest reconfiguring xserver-xorg or changing /etc/X11/xorg.conf which I have done (see below), but it doesn't help: GDM still choses a resolution not in my xorg.conf file.

I've been chasing these two independently, until somebody suggested to try the "vesa" driver. When I do, the GDM login screen automatically uses 1600x1200 resolution. ( However, with the "vesa" driver, the bottom inch of the screen is garbled, both on the login screen and after I've logged in. )

So now I'm thinking that the login screen resolution is a problem with the "intel" driver. Is anybody else seeing this or does anybody have a fix / workaround? Does anybody know how to get the vesa screen looking properly?

I would like to file this as a bug against xserver-xorg-video-intel, and will do so if I don't hear otherwise, but I don't understand how the GDM resolution could be bug with xserver-xorg-video-intel, when it works fine after login...

Peter

Here are what I think are the relevant portions of xorg.conf. (see attachments for the whole thing)
```

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	30-81
	VertRefresh	56-75
	ModeLine       "1600x1200" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Option         "UseEDID" "False"
	Option         "DPMS"
	# Option         "HWCursor" "off"
	Option         "DPI" "109 x 109"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200"
	EndSubSection
EndSection
```

(The attachment contains xorg.conf and Xorg.0.log for both intel and vesa drivers)

---

### Post by 3xhacks on 2008-03-08
is the resolution at the desktop 1600x1050?

---

### Post by pmorch on 2008-03-08
> **3xhacks said:**
> is the resolution at the desktop 1600x1050?

At the point with the GDM login screen, there is no desktop yet. At that point, I am certain it is not 1600x1200, because that is the LCD's native resolution, and it looks blurry because it is a different resolution. I don't know how to see what resolution it is running at, and I don't know how to find out. There is nothing in X.0.log and there "DISPLAY=0:0 xwininfo -root" (which will normally tell my resolution) doesn't succeed in contacting the X server. So the short anwer is "I don't know and I don't know how to find out" - but it looks lower resolution would be my guess.

My desktop, once I've logged in properly is running at 1600x1200, just like it should.

Peter

---

### Post by 3xhacks on 2008-03-08
try here [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/16472](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/16472)

---

