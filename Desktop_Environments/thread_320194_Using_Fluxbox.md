---
title: "Using Fluxbox"
date: 2006-12-16
forum: Desktop Environments
---

### Post by koolkid64us on 2006-12-16
OK, I figured it out.  New question.



How do I change my screen resolution in Fluxbox?

---

### Post by koolkid64us on 2006-12-16
Any help would be greatly appreciated.;)

---

### Post by kerry_s on 2006-12-17
In fluxbox you would have to do it manually, but i'm assuming you have gnome installed, so just switch to gnome and use the display settings tool.

For manual, from terminal->
sudo gedit /etc/X11/xorg.conf

 	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
 
Add or subtract the resoulution you want.

---

