---
title: "Running Mame with a launcher"
date: 2008-02-19
forum: Gaming &amp; Leisure
---

### Post by optimal on 2008-02-19
After reading about the many frontends for Mame I decided that the best option is to ditch the frontend nonsense and just use good old launchers to do the dirty. Realistically this is the most minimal approach...

====== Install XMAME ======

[LIST]
[*]System
[*]Administration
[*]Synaptic Package Manager
[*]Search "xmame"
[*]Tick xmame-sdl
[*]Bing Bang Bong
[/LIST]
====== Download a ROM and some ICONS ======

Grab a ROM from here:
[mamedev.org]("http://mamedev.org/roms/")

Icons from here
[mameworld.net]("http://www.mameworld.net/icons/pages/mameicons.html")

====== Create your launcher ======

Assuming xmame is installed OK, you have your ROM (my example shows Robby Roto), and your icons are unpacked somewhere, all you need do is create a launcher to run your game...

[LIST]
[*]Open up a text editor and paste in the following:
[/LIST]
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Robby Roto
Type=Application
Terminal=false
Exec=/usr/games/xmame /home/david/Desktop/Games/roms/robby.zip -fullscreen
Icon=/home/david/Desktop/Games/roms/robby.ico
```
[LIST]
[*]You will need to make sure the three paths are correct;
[LIST]
[*]**/usr/games/xmame** - I *think* this is the default install path for xmame
[*]**/home/david/Desktop/Games/roms/robby.zip** - path to your ZIP file
[*]**/home/david/Desktop/Games/roms/robby.ico** - path to your icon file
[/LIST]
[*]Save the file somewhere as **robby.desktop** and hopefully a neat, working launcher will be created! Chuck it into a menu, panel, folder whatever!
[/LIST]

====== Nota Bene ======

[LIST]
[*]I am totally new to ubuntu / linux, if a boffin thinks this is a terrible method, just let me know, am happy to learn!
[*]Also, is there a way of using **~/Desktop...** syntax in launchers? I couldn't get that to work!
[*]MAME is not 100% working, of the ROMS you try, expect at least half of them to fail!
[*]<snip> - slow, but OK!
[/LIST]

====== Peace, David King ======

---

### Post by K.Mandla on 2008-02-19
Moved to Games and Leisure.

---

### Post by optimal on 2008-02-19
Thanks K.Mandla!

---

### Post by pud_face on 2008-11-17
hi i am totally new to ubuntu i copied all the stuff from your text editor and use my info like where i put it and so on but i save it and it does nothing can you help plz

---

