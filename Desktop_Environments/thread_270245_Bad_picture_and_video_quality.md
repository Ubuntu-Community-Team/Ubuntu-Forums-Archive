---
title: "Bad picture and video quality"
date: 2006-10-02
forum: Desktop Environments
---

### Post by eklypse on 2006-10-02
I'm not too sure what happened but I think it has to do with my video driver.  I have dapper and a toshiba a10 laptop and now my pictures and videos all look like crap.  I will have wavy lines, it looks like the quality turn way down on a video.  It looks like I am looking through a greasy film when viewing pictures and video, but everything else looks fine.  I makes everything look like garbage.  I have no idea what has caused this or where to start.  any ideas?

---

### Post by wieman01 on 2006-10-03
Perhaps a wrong driver? Could you show us what system you're using and what hardware you have? Hard to tell what's going on without a few more particulars.

---

### Post by eklypse on 2006-10-03
I have a toshiba laptop a10 and using ubuntu dapper.  How can I install a toshiba a10 graphics driver??  only the pictures and video are affected, the actual Gnome GUI is fine.

---

### Post by wieman01 on 2006-10-03
The PC model won't help much. Can you try to find out what graphic card is built in?

---

### Post by eklypse on 2006-10-03
I have a  Intel Corporation 82852/855GM Integrated Graphics Device

I think I do anyways.  Every programs runs normal but if I view a picture or video it doesnt work.  I had xgl and compix installed and I unistalled them in synaptic package manager. If that helps.  Thanks ahead of time for any help.

---

### Post by wieman01 on 2006-10-03
Yes, perhaps there is something you could do. I have got the same device. Can you change the "default depth" of your GUI for a minute? The file I am referring to is this:
> sudo gedit /etc/X11/xorg.conf
There is a section that looks similar to this:
> Section "Screen"
	Identifier	"Internal Screen"
	Device		"Internal Device"
	Monitor		"Internal Monitor"
	DefaultDepth	**[COLOR="Red"]16[/COLOR]**
	SubSection "Display"
		Depth		**[COLOR="Red"]16[/COLOR]**
		Modes		"1280x768"
	EndSubSection	
EndSection
You could try & change the DefaultDepth from 24 to 16 or the other way around. Remeber that you have to edit 2 lines in that case (in red). Then restart the X-server ("crtl + alt + backspace"). Does that help?

---

### Post by eklypse on 2006-10-03
still have the problem.  I have:

> Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

and I changed it to:

> Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	[COLOR="Red"]16[/COLOR]
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		[COLOR="Red"]16[/COLOR]
		Modes		"1024x768"
	EndSubSection
EndSection

Didn't fix it.](*,)

---

### Post by wieman01 on 2006-10-03
Actually I was wrong in that you have to change "Depth" to 16 as well... Since you have a number of option already (1, 4, 8, 15, 16, 24) there is no need to do that. 

You control the depth by editing this line:
> DefaultDepth xx
...whereas the options further below must correspond to the depth you have chosen.

You can try other settings as well, but if this does not do the job I am afraid I cannot help any further. Your graphic card/device has definitely been recognized ("Intel Corporation 82852/855GM Integrated Graphics Device") which is the good news.

---

