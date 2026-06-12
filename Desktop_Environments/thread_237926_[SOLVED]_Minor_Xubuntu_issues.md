---
title: "[SOLVED] Minor Xubuntu issues"
date: 2006-08-16
forum: Desktop Environments
---

### Post by deepgray on 2006-08-16
Hello folks,

I've been using Xubuntu Dapper for about a month now and am very pleased with the OS. I have a short list of issues that I have been unable to resolve, however.

1) My desktop is set to 1024x768. When exiting some full-screen apps (various games) running at 640x480, the desktop does not return to the original resolution. The desktop remains at 640x480 and appears magnified. Moving the mouse cursor to the edges of the screen 'pans' the viewable portion of the desktop. 

Also, when exiting some other full-screen apps the desktop returns to 1152x864. This resolution seems to be the same as the top 'Default' item in the Xfce Settings -> Display Settings resolution list (as an aside, is there a way to change this default resolution?).

2) Thunar shortcuts (Ctrl+B) disappear if the device they link to is unmounted, and do not reappear if the device is mounted again. (Aside: Where are these shortcuts stored?) I would prefer the shortcuts to either remain or to reappear when mounting in lieu of the current behaviour.

Thank you for your support!

---

### Post by Predius on 2006-08-16
> 
Also, when exiting some other full-screen apps the desktop returns to 1152x864. This resolution seems to be the same as the top 'Default' item in the Xfce Settings -> Display Settings resolution list **(as an aside, is there a way to change this default resolution?).**

Just look in your /etc/X11/xorg.conf. The leftmost resolution is the default one.

---

### Post by deepgray on 2006-08-16
Thanks for your rapid reply!

Looking in xorg.conf was my first idea, but regarding your comment, I'm not sure what of the below should be changed. As to this issue, I would like the default to be 1024x768@85 as displayed in the list of available resolutions in display settings.

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 Pro Ultra TF"
	Monitor		"NEC FE700+"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

### Post by deepgray on 2007-09-19
Marking thread as solved because I have not encountered these issues since 7.04.

---

