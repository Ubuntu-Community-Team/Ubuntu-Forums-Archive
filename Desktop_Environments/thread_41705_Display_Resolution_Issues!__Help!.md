---
title: "Display Resolution Issues!  Help!"
date: 2005-06-14
forum: Desktop Environments
---

### Post by orev on 2005-06-14
I would like to be running 1280x1024 display resolution (at min) on my Kubuntu box, but I don't seem to be able to update or change this quantity.

I am a bit new, but trying to migrate away from WinXp entirely (or almost - really like Photoshop, Dreamweaver, and itunes). 

Can someone point me in the right direction to change the display settings in Kubuntu?

(I have looked at documentation and Faq, so if I've just missed this, please post a url - thanks!)

---

### Post by rachii on 2005-06-14
edit your xorg.conf and add the resolutions you want.

  sudo gedit /etc/X11/xorg.conf

then scroll down to the bottom, under the section "screen" there is SubSection "display" that should have resolutions listed...just add yours, and then save.

then hit ctrl+alt+backspace to restart X.... log in and you should be able to change the resolutions

---

### Post by orev on 2005-06-14
Thank you very much for the reply.

I started with this:

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Monitor		"hp mx703"
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

AND I added this:

	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection


I restarted x(?), but I am not able to change to 1280x1024.  Did I do this incorrectly?

url or more advice please?!?

---

### Post by Xian on 2005-06-14
Scroll up that xorg.conf and post the "Monitor" section.

---

### Post by orev on 2005-06-14
Call me new....but...

Post the "Monitor" section?

I guess I'm not sure what you mean/how to do this?

This is what I have in the monitor section:

Section "Monitor"
	Identifier	"hp mx703"
	Option		"DPMS"
EndSection


I don't see where to make a change to this...

Your kindness will be repaid...   :)


(if this is all in a document page or faq, please point me to the url)

---

### Post by Xian on 2005-06-14
[QUOTE=orev]Section "Monitor"
	Identifier	"hp mx703"
	Option		"DPMS"
EndSection[/QUOTE]

You did just fine. And this is where your problem resides.

You don't have any refresh/sync rates in that section, so your resolution is unable to be set to anything other than what the current configuration can support. Basically, you need to pull out or look up your monitor specs and then add the applicable rates to the xorg.conf file in the section you just provided. You might also want to provide the display size as well since this will also be helpful. Here is a good [How-To](http://www.advogato.org/person/robertc/diary.html?start=35) on that subject.

Listed below is my own "Monitor" section. 
You can use it as a guide but of course don't duplicate the settings.

```
Section "Monitor"
	Identifier	"COMPAQ 7500"
	Option		"DPMS"
        HorizSync       30-70
        VertRefresh     50-140
        DisplaySize     312 234
EndSection
```

---

### Post by jeremy on 2005-06-15
[QUOTE=orev]Thank you very much for the reply.

I started with this:

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Monitor		"hp mx703"
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

AND I added this:

	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection


I restarted x(?), but I am not able to change to 1280x1024.  Did I do this incorrectly?

url or more advice please?!?[/QUOTE]
 Rather than adding 

SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

you should add "1280x1024" before "1024x768" in the existing sections.

---

