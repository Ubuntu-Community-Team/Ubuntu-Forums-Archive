---
title: "GDM resolution"
date: 2005-05-01
forum: Desktop Environments
---

### Post by Linforcer on 2005-05-01
When I first installed Ubuntu the deafault resolution was 1280x1024, I quickly changed that to 1152x864 because the 60Hz hurt my eyes.

Anyway, my GDM login screen still ran at 1280x1024, so I changed the default resolution is xorg.conf to 1152x864 too, but now, I get a gdm login I can scroll. 

You know, where you move the mouse to the edge of the screen and it scrolls, sio it seems the graphical greeter doesn't pick up on what resolution X is using.

How can i fix that?

---

### Post by Alexander Kirillov on 2005-05-02
[QUOTE=Linforcer]When I first installed Ubuntu the deafault resolution was 1280x1024, I quickly changed that to 1152x864 because the 60Hz hurt my eyes.

Anyway, my GDM login screen still ran at 1280x1024, so I changed the default resolution is xorg.conf to 1152x864 too, but now, I get a gdm login I can scroll. 

You know, where you move the mouse to the edge of the screen and it scrolls, sio it seems the graphical greeter doesn't pick up on what resolution X is using.

How can i fix that?[/QUOTE]
 Can you post your xorg.conf file here?

---

### Post by Linforcer on 2005-05-02
I'ts pretty much the basic but with Nvidia commercial drivers and the first two resolution switched. 
I could just switch the resolutions back, but I don't want my eyes to hurt every time I need to log in :S

Erm, I uploaded the xorg.conf... I think...

---

### Post by cdhotfire on 2005-05-02
try changing all depths to "1152x864" from 1-16, and try again.:)

---

### Post by Alexander Kirillov on 2005-05-02
I think the problem is here: 
```
SubSection "Display"
		Depth		24
		Modes		"1152x864" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
```
SInce you have 1280x1024 among the list of modes, Xserver creates "virtual screen" of size 1280x1024. Then it switches to 1152x864 which only shows portion of this "virtual" screen. 

I'd bet that removing 1280x1024 from this list will solve the problem. There should be more elegant ways of dealing with it, but this should work, too.

---

### Post by cdhotfire on 2005-05-02
[QUOTE=Alexander Kirillov]I think the problem is here: 
```
SubSection "Display"
		Depth		24
		Modes		"1152x864" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
```
SInce you have 1280x1024 among the list of modes, Xserver creates "virtual screen" of size 1280x1024. Then it switches to 1152x864 which only shows portion of this "virtual" screen. 

I'd bet that removing 1280x1024 from this list will solve the problem. There should be more elegant ways of dealing with it, but this should work, too.[/QUOTE]

lol, i didnt see that, good eye.;-)

---

### Post by Linforcer on 2005-05-03
All good. Sort of strange that it just uses the biggest resolution in the list :S:S:S

---

