---
title: "Resolution Problems?"
date: 2005-02-07
forum: Desktop Environments
---

### Post by totalshredder on 2005-02-07
Hey Everybody,

   When I was installing ubuntu, at the end the installer asked what resolutions I would like to use. So I checked a few off and continued on in the install. Problem is, I don't think I chose enough resolutions, I would like to have more options so I can possibly go higher in my resolution. What can I do? How can I get back to that screen where you chose your resolutions?

Thanks!!

Luke Demi

---

### Post by Razvan on 2005-02-07
depending on the xserver you have installed, config files are /etc/X11/XF86Counfig-4 or /etc/X11/xorg.conf you can find a section like this

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"00e6"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

obviously, you can add resolutions here :-)

also i think there is a command like base-setup to run this thing that does the configs again but i dont know for sure

---

### Post by RichardA on 2005-02-08
The command is something like (I'm at work, this is from memory):

sudo dpkg-reconfigure xserver-xfree86

The current settings are shown as the defaults, so only change the one(s) you want.

Also, I'd log out, change to a different terminal, make the change, change back to the login screen and do CTRL-ALT-BACKSPACE to restart the X server. Not very elegant, that last bit!

---

