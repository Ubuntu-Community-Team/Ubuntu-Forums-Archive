---
title: "Half Life 2 Menu Glitch"
date: 2007-04-04
forum: Gaming &amp; Leisure
---

### Post by SilverSkulls on 2007-04-04
Hi,

I have recently installed Steam and Half Life 2 through Wine on my Ubuntu 6.10 system.  I copied all of the core windoze fonts (including tahoma.ttf, verdana.ttf) to my ~/.wine/drive_c/windows/fonts/ folder.  I also copied them to my /usr/share/fonts/ folder for good measure.  When I run Steam through Wine, all of the text is clearly visible as it should be, but when I then launch HL2, the main screen's text is missing for the menus (New Game, Load Game, Options, etc.).  The title "Half Life 2" is visible.  Does anyone know what could be the problem?  It is a bit annoying having to guess where the text is and go by the audio to find the correct buttons.  The rest of the game (a.k.a. not the menus) works perfectly. 

Thanks,
-SilverSkulls-

---

### Post by SilverSkulls on 2007-04-10
bump...

---

### Post by FoolsGold on 2007-04-11
Since you can view the text used in Steam, the fonts should work just fine in HL2, so that's probably not the issue. I suppose the only advice I can give is to ensure you have got the latest version of Wine installed, and the latest video drivers. 

If you're desperate you could clear your wine config and start fresh.

---

### Post by lordhebe on 2007-04-11
Try installing the msttcorefonts package. the .deb file is here [http://packages.ubuntu.com/edgy/x11/msttcorefonts]("http://packages.ubuntu.com/edgy/x11/msttcorefonts")

---

### Post by SilverSkulls on 2007-04-11
Thanks for your help guys.  Installing the bleeding-edge nvidia video drivers and reinstalling the windoze fonts seems to have done it! =D>

---

