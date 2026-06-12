---
title: "Location of Chrome folder for Firefox in Wine"
date: 2006-07-05
forum: Desktop Environments
---

### Post by jinks on 2006-07-05
Hi, I'm trying to get the Windows version of Firefox running in Wine.  I have custom userChrome.css, userContent.css, and user.js files that I use.  I know where to put them in Windows and in Linux, but I have no idea where to place them in Wine.  Can anyone help?  I'm hoping it's a no brainer path that's easy to find. :)

Also, can I set the default font in Wine?  It seems to use Times New Roman in the IE and Firefox menus and other software as well.  I want to set it to Arial or something else.

---

### Post by mannheim on 2006-07-05
I can help with the font question, I think. You are getting Times in the menus because under wine the application isn't finding Tahoma or whatever it expects. You can copy all the genuine windows fonts to ~/.wine/drive_c/windows/fonts and you should be okay. Alternatively, if like me you have a real windows installation on some mounted ntfs partion somewhere, you can make ~/.wine/drive_c/windows/fonts a symlink to the genuine Windows/Fonts folder. 

It worked for me. I also put the Windows/Resources/Themes into .wine/drive_c and then used winecfg to select the default Winows XP "Luna" theme. Now apps running under wine have Tahoma fonts (or whatever) and an XP look to them.

---

### Post by mannheim on 2006-07-05
Ah, and the Firefox profile is in

```
"$HOME/.wine/drive_c/windows/profiles/[COLOR="Blue"]USERNAME[/COLOR]/Application Data/Mozilla/Firefox/Profiles"
```

---

### Post by jinks on 2006-07-06
Thanks a bunch!  The profile location for firefox worked perfectly.  And I took your advice and copy/pasted all the fonts off of my windows machine into wine, but it doesn't change the appearance in the firefox menus, although it seems to have worked for Internet Explorer, so that's a start.  But then I never really paid attention to how IE looked in the first place, hehe.

---

