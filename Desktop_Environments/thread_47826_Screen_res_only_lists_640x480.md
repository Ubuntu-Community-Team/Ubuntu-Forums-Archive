---
title: "Screen res only lists 640x480"
date: 2005-07-10
forum: Desktop Environments
---

### Post by tonyvfield on 2005-07-10
I have just installed ubuntu, and the screen resolution is set to 840x480. Fine but the challenge is that on the form to change the resolution there are no other options to choose from. The pull down list does not allow me to change it to anything else. My screen I know will go to 800x600. How do I over ride the options?
Simple instrcutions please as I am new to Linux

Regards
Tony

---

### Post by SS2 on 2005-07-10
Hi,

do you have a TFT?

could be that in your xorg.conf file there is something missing. I have the same problem wenn I also install my Hoary.

Here is maybe something what you need but is maybe not in youre /etc/X11/xorg.conf:

```
Section "Monitor"
        Identifier      "DELL E152FP"
        HorizSync       30-63
        VertRefresh     56-76
#       Option          "DPMS"
EndSection

```

---

### Post by Leif on 2005-07-10
There are two ways you can do this. But before doing anything else, you should backup your configuration. Do this with "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup". Later, if you make a mistake, you can copy the file back and you'll have your configuration back.

The first method is to run "sudo dpkg-reconfigure xserver-xorg", and at the appropriate point of the process make sure you tick your desired resolution too.

The second is to run "sudo gedit /etc/X11/xorg.conf". Now scroll down to the part where resolutions are specified, and put a 800x600 next to the 840x480. In my case, that section looks like this :

SubSection "Display"
Depth           16
Modes           "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth           24
Modes           "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

---

### Post by tonyvfield on 2005-07-10
Many thanks for the help so far, but still puzzled. I have copied below the contents of the xorg.conf file which does show the resolutions, that I want. So a little more help please. 
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. 3D Rage Pro (AGP)"
	Monitor		"DELL P791"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Regards 

Tony

---

### Post by tonyvfield on 2005-07-10
Sorry I should also state that I have an NEC Multisync XP17 screen.

Tony

---

### Post by Leif on 2005-07-10
According to this page ([http://www.monitorworld.com/Monitors/nec/multisyncxp17jc1743uma.html](http://www.monitorworld.com/Monitors/nec/multisyncxp17jc1743uma.html)) your monitor will go up to 1600x1200, but you may need to change your monitor settings. Try :

Section "Monitor"
        Identifier      "DELL E152FP"
        HorizSync       31-82
        VertRefresh    55-160
       Option          "DPMS"
EndSection

And restart X (you can do this with ctrl+alt+backspace. Afterwards, try ctrl+alt+plus or minus to cycle through available frequencies and see if it works.

---

### Post by Irony on 2005-07-10
I recently had the same problem.

To solve it I right clicked in an empty area of the desktop and clicked Open Terminal and then typed in the following;

sudo gedit /etc/X11/xorg.conf

This opened the xorg.conf file, I scrolled down to the Monitor section which originally didn't have HorizSync VertRefresh numbers. I altered it so it looked like the following;

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72

I got the correct HorizSync VertRefresh figures by using the Live CD which had the correct resolution. In other words I booted from the Live CD opened a Terminal and typed;

gedit /etc/X11/xorg.conf

and then noted the correct figures.

*Thus if your Live CD has the correct resolution use it to find the correct figures, whether they be HorizSync VertRefresh or any of the other numbers.*

Note sudo means superuser and allows you to change the file. gedit opens the file in gedit a text editor.

---

### Post by tonyvfield on 2005-07-10
I will try that when I get back from Spain. Now the issue is that I need the SU password, which between me and the guy who installed it, we have forgotten. Stupid I know.
The reason for needing the SU password is that I made the edits as above and now the system wont boot into the graphics mode so I need to replace the file with the backup.

Anyway back on Wednesday and will try installing again and then will sort this out.

Thanks folks

Tony

---

