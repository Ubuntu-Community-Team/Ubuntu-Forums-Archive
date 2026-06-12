---
title: "Help with login screen"
date: 2006-03-01
forum: Desktop Environments
---

### Post by MrDan on 2006-03-01
when I installed Ubuntu, the desktop was first set to 1600 x 1200 which my monitor doesn't do, so it goes off the screen and you have to mouse over to see edges.  I changed the desktop resolution to 1280 x 1084 and it is great.  Now my problem is that the login screen is still stuck on the 1600 x 1200 option and it is getting old.  I am having trouble finding where you change the resolution for the login screen.  Please help!!!:-k

---

### Post by rubicon05 on 2006-03-02
Mr Dan, I found this in the archives.  It may be some help to you:

[http://ubuntuforums.org/archive/index.php/t-76387.html](http://ubuntuforums.org/archive/index.php/t-76387.html)

Regards,
Rob

---

### Post by MrDan on 2006-03-02
Thanks! 

Still no luck. My graphic card is not nvidia and the /etc/X11/xorg.conf I couldn't see any thing wrong.. I restart and still the login screen overlaps the monitor so I need to move the mose off the screen to move the view to see the rest.

Hmm, this is a tricky thingie-poo.:-k :confused:

---

### Post by noomz on 2006-03-02
you can try to change setting in 'xorg.conf' in Section "Screen" to this

        ```
SubSection "Display"
                Depth           1
                Modes           "1280x1084" "1024x768" "800x600" "640x480"
        EndSubSection
```

i hope it may help ... ;)

---

### Post by noomz on 2006-03-02
Oh!..Sorry in 'Depth' It's migth be any depth u want

```
SubSection "Display"
                Depth           16  // can and this subsection many times
                Modes           "1280x1084" "1024x768" "800x600" "640x480"
EndSubSection
```

---

### Post by MrDan on 2006-03-02
This is what is currently in the screen section:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Device"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection



I deleted the 1600 x 1200 out of all the modes thinking that might work. but alas! :-?

---

### Post by MrDan on 2006-03-02
Ok I bounced (hard rebooted) my box and now its good.\\:D/  Thanks all!

---

