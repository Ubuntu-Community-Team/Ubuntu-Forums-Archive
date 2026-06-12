---
title: "Black Desktop Background even when image set"
date: 2013-11-26
forum: Desktop Environments
---

### Post by chrissie-c-l on 2013-11-26
[ATTACH=CONFIG]248120[/ATTACH]
So previously I was having image backgrounds, but today (can't remember what I was doing when it changed, I have been having a lot of windows open) I now have a black background, even though the system settings tool shows that I have an image background.  

Didn't run any system updates today, though I have been installing a bunch of new programs, and added a new user.

---

### Post by duronjoshua on 2013-11-26
Try this: 

[COLOR=#000000][FONT=Ubuntubeta]sudo gsettings set org.gnome.desktop.background show-desktop-icons true; [/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntubeta]sudo gsettings set org.gnome.desktop.background show-desktop-icons true;[/FONT][/COLOR]

---

### Post by chrissie-c-l on 2013-11-26
Nope.  Things also seem to freeze up a bit when I try to change background settings.

---

### Post by Frogs Hair on 2013-11-27
A black background can appear if the location of the image file was changed . You might try going to the image folder and setting the image again if it was moved. Under wallpapers in appearance preferences you can also use the + symbol to navigate to the image folder. In the Tweak Tool if installed  make sure the file manager is set to handle the desktop. A simple way to check this setting is if you right click the desktop and if the context menu _doesn't_  appear the setting is turned off. Another option is to restart Nautilus . ```
nautilus -q  
```

---

