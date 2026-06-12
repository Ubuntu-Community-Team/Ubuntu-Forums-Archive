---
title: "XFCE screen settings do not stay upon reboot"
date: 2009-06-02
forum: Desktop Environments
---

### Post by scanman717 on 2009-06-02
I have a Jaunty install, running XFCE...  It is connected to my TV VGA input.  I need to output at 1024x768 @ 75hz.

When the system reboots, I have to hook up  a monitor and reset this back to what I need, then connect back to the TV... Needless to say this is a huge PITA!!

Does this use xorg.conf file?/ That file seems almost empty.. Where else can I go to hard code this setting so that it remains on boot up??

Thanks!!

Troy

---

### Post by kerry_s on 2009-06-03
yeah, you would have to add to the xorg.conf

example:

```
Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync 	31-81
	VertRefresh 	56-75.1
EndSection
```

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1024x768"	
	EndSubSection
EndSection
```

---

### Post by scanman717 on 2009-06-03
Did that.. No love...  Looked at the xorg.conf file and it reverted back to a very generic file...  Soooo... Where else can I look for settings to make what I need stick?


Thanks

---

### Post by kerry_s on 2009-06-03
> **scanman717 said:**
> Did that.. No love...  Looked at the xorg.conf file and it reverted back to a very generic file...  Soooo... Where else can I look for settings to make what I need stick?


Thanks

it reverted? did you edit it as root?(alt+f2, gksudo mousepad /etc/X11/xorg.conf)

---

### Post by scanman717 on 2009-06-03
Well, that may be part of the problem. I am doing this editing via SSH connection to the box and then sudo nano /etc/X11/xorg.conf

Save then shutdown -r now

Still no video output. I can see the bios messages, splash screen, then nothing.....

---

