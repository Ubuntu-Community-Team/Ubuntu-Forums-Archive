---
title: "Accessing files in wine"
date: 2007-07-09
forum: Gaming &amp; Leisure
---

### Post by Ziggyz on 2007-07-09
Is it possible to access folders in wine whereas I can put files in and out of there manually? Say if I wanted a skin for counterstrike... Or a mod for world of warcraft.
Also when ever I alt tab out of games it freezes up my computer, any way to stop that?

---

### Post by Programmerer on 2007-07-09
> Is it possible to access folders in wine whereas I can put files in and out of there manually? Say if I wanted a skin for counterstrike... Or a mod for world of warcraft.

Wine emulate a drive in /home/username/.wine/drive_c.
Just open you're home folder, press Control+H for to show the hidden files, open .wine, and then drive_c, and there will you find the files that are on disk "C:\" in wine.

---

### Post by cogadh on 2007-07-09
Wine stores the files you install in the hidden .wine directory, when you open your home folder, just press CTRL-H and it will be shown. The structure of the .wine folder is just like a Windows hard drive.

EDIT - Programerer types faster than me, apparently.

---

### Post by Ziggyz on 2007-07-09
Aight cool, but what about the computer freeze? I enabled the nvidia stuff, how can I see if I have drivers installed? (Sorry, newb to linux and ubuntu)

---

### Post by cogadh on 2007-07-09
Wine doesn't handle the "ALT-TAB" function well. I recommend you don't do it or set Wine to emulate a virtual desktop, if you need to get back to your desktop while gaming.

---

### Post by Programmerer on 2007-07-09
Open Restricted Drivers Manager in System>Administration, and check if it is enabled.

---

### Post by Ziggyz on 2007-07-09
Yeah its enabled, and that means that my drivers are up to date? How would I set up a virtual desktop? (Thanks again for the info guys)

---

### Post by cogadh on 2007-07-09
Since you installed the drivers from the Ubuntu repositories then they are as up-to-date as they generally need to be.

Run "winecfg" in a terminal, click on the Graphics tab and check the Emulate virtual desktop box. Make sure the resolution is set at at least 800x600.

---

