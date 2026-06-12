---
title: "Desktop res change won't stick on reboot"
date: 2007-03-26
forum: Desktop Effects &amp; Customization
---

### Post by theragu40 on 2007-03-26
Hello,

I am using a Geforce 6800XT with the latest nvidia drivers.

I want to change my resolution to default to 1280x1024, since that is the native resolution of my monitor.  I am able to change to this setting via the nvidia control panel, but it is not listed as an option in System>Preferences>Screen Resolution.  Every time I reboot my machine, I have to reset the setting.  It's not a huge deal, since it's not like I'm rebooting all the time, but it's an annoyance thing.  

I'm pretty much a noob when it comes to ubuntu, so I'm not really sure how to troubleshoot this myself.  I assume I have to edit something in the xorg.conf file or something...but I wanted to come on here and ask people who know what they're doing first.

Thanks in advance!

---

### Post by dannyboy79 on 2007-03-26
yes, you should just have to add that option to your /etc/X11/xorg.conf file. first always make a backup of it, do this for every file you ever change, this way if you screw up, you can always boot to recovery mode or even frmo a live cd and just replace the bad new file with the old backup. So you'll want to open this file up using sudo so that you can edit and save it and add 1024x1024 as an option under this area:

SubSection "Display"
	Depth		1
	Modes		"1360x768" **"1280x1024"** "1024x768" "800x600" 
EndSubSection
SubSection "Display"
	Depth		4
	Modes		"1360x768" **"1280x1024"** "1024x768" "800x600"
EndSubSection
SubSection "Display"
	Depth		8
	Modes		"1360x768" **"1280x1024"** "1024x768" "800x600"
EndSubSection
SubSection "Display"
	Depth		15
	Modes		"1360x768" **"1280x1024"** "1024x768" "800x600"
EndSubSection
SubSection "Display"
	Depth		16
	Modes		"1360x768" **"1280x1024"** "1024x768" "800x600"
EndSubSection
SubSection "Display"
	Depth		24
	Modes		"1360x768" **"1280x1024"** "1024x768" "800x600"
EndSubSection


and you should be good to go.

---

### Post by theragu40 on 2007-03-26
Marvelous, thank you very much.  I've got class now, but I will definitely be giving that a shot when I get back.  I appreciate it!

---

