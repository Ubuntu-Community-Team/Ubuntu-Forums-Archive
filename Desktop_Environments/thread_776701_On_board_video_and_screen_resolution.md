---
title: "On board video and screen resolution"
date: 2008-04-30
forum: Desktop Environments
---

### Post by cign on 2008-04-30
Hi everyone.  I just started using Ubuntu a couple of weeks ago so I'm still learning the inns and outs.  I have a question in regards to Ubuntu 8.04.  Every time I log on the screen resolution always seems to default to 1280x1024.  I can change it back to 1024x768 but the next time I start up my computer the resolution defaults back to 1280x1024.  I don't recall having this issue with 7.10.  The video card is on board so I'm not sure what to do or how to load any drivers for it.  Appreciate any help or suggestions.


Thanks, 

Chris

---

### Post by gnuskool on 2008-05-01
Give specific info for a quicker answer, Chris, like

- the name of the graphics card, manufacturer
- laptop or desktop


stuff like that, just so it's narrowed down and also, people with the same cards can find it by searching those names

---

### Post by cign on 2008-05-02
I have no idea what the video card would be.  I'm assuming it's an intel brand.  All I can tell you is that I'm running Ubuntu 8.04 on an older Compaq Evo.  It's a pentium 4 1.8GH.  Hope this helps a bit. Will the BIOS tell you the type of videocard?  Since it's an on board video card is there anything on the motherboard indicating the video card.  My other option which I was debating is to buy an older ATI or NVIDIA card.  If I decide to go with another video card which one plays better with UBUNTU?

Thanks,

Chris

---

### Post by Zorael on 2008-05-03
If you decide to go with a new card, pick Nvidia for linux use; ATI drivers may be up-and-coming, but for the time being, Nvidia drivers are superior.

As for screen resolution, X (the graphical environment) auto-detects available resolutions and automatically picks the highest one. If you provide the contents of your **/etc/X11/xorg.conf** file we should be make slight alterations to limit the maximum to 1024x768.

In 7.10 it relied more on defined settings (in mentioned file) rather than auto-detection.

---

### Post by cign on 2008-05-06
I'm having a bit of trouble with xorg.conf  I ran your command in terminal but I get permission denied.  I'm very new to Ubuntu and haven't figured my way around yet.  Can you please let me know how to display xorg in terminal?

Thanks,

Chris

---

### Post by Zorael on 2008-05-07
Well, you can show your xorg.conf file in a graphical editor by opening a run box (Alt+F2) and entering **gedit /etc/X11/xorg.conf**.

If you get 'permission denied' messages that's likely since whatever you tried to do required superuser permissions, which can be attained by prepending **sudo** before the command (or **gksu** if it's a graphical command, like gedit).

But you don't want to go around sudoing everything, it should only be used when you know what you're doing. Else you'll break stuff.

---

### Post by cign on 2008-05-08
Thank you for clearing that up and for the xorg command.  Here's the output.  I hope that this will help in figuring out how to permanently set my resolution to 1024x768

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by Zorael on 2008-05-09
Modifying the Screen section to the following should limit max resolution to 1024x768.
```
Section "Screen"
	Identifier "Default Screen"
	Monitor "Configured Monitor"
	Device "Configured Video Device"
[B]	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
[/B]EndSection
```

---

### Post by cign on 2008-05-09
I'll make the changes later on today and I'll let you know how it works out. Thanks for your help, I appreciate it.

---

### Post by cign on 2008-05-09
I changed my config based on your reccomendations and it works great.  Thank you.  Is there somwhere on the web info on some of the most popular Ubuntu comands or a book that might make it easier for someone new to learn more about it.

---

### Post by PhatKat on 2008-05-11
Wow luckily i stumbled across this thread so there is hope for me hehe. I had DIYed a buntu box a fortnight ago and my original intention was to run butu 8.04LTS. However my mobo with VIA IGP (K8M800) gives weird options in the screen resoulution options: either i can set it ti a huge 1440 x 900 or a tiny 640 x 480 ahhhh! You think your work around would also apply to me? Am running the box with Gutsy and everything's fine - but IMO wifi works better in Hardy though....

---

