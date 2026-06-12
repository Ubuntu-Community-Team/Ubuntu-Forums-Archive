---
title: "Increase screen resolution"
date: 2007-09-14
forum: Dell  Ubuntu Support
---

### Post by mikecomua on 2007-09-14
Hi, I have a Dell Inspiron e1405 with a beautiful 14.1 1440x900 pixels resolution. I love Ubuntu, but I would like to increase my resolution to at least 1280 x1024. Strange thing is when I boot into puppy my resolution is 1440x900. I can't reconfigure my xorg.conf file because I have no idea which parameters my screen has. Can I copy my xorg.conf file from puppy and paste it into my Ubuntu? THX

---

### Post by magiceraser06 on 2007-09-21
Mike.

if your display is coming up at 1440x900, you shouldn't have to worry about the parameters.  
```

sudo gedit /etc/X11/xorg.conf
```


then scroll down until you see the section SCREENS,  see my exerpt of my xorg.conf file
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage Mobility M3 AGP 2x"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

Just make the line MODES in your xorg.conf file look like mine.  If you want, you can also add in the line "1440x900" before the "1280x1024" entry. 

REBOOT and you should be able to then select which resolution you wany by going to SYSTEM----> PREFERENCES ----> SCREEN RESOLUTION.

Hope that helps.

---

### Post by girishkolari on 2007-09-21
Why don't try installing 915resolution.
here is the help to use this 
[http://girishkolari.blogspot.com/2007/08/fix-resolution-problem-in-dell-inspiron.html]("http://girishkolari.blogspot.com/2007/08/fix-resolution-problem-in-dell-inspiron.html")

---

