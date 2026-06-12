---
title: "[SOLVED] How do I instal DOFUS to my Ubuntu"
date: 2007-05-06
forum: Gaming &amp; Leisure
---

### Post by waggygee on 2007-05-06
I just downloaded DOFUS_v1_18_1.zip file. I am new to the linux operating systems. What do I do with it next in order to get the game running?

---

### Post by Perfect Storm on 2007-05-06
Check our Installation guides: [http://gaming.gwos.org/e107_plugins/content/content.php?content.19](http://gaming.gwos.org/e107_plugins/content/content.php?content.19) (which are linked in our sticky in this forum).

---

### Post by waggygee on 2007-05-06
Afer typing alacarte compand this happens:

(alacarte:8414): Gdk-WARNING **: locale not supported by Xlib

(alacarte:8414): Gdk-WARNING **: cannot set locale modifiers

(alacarte:8414): GnomeUI-CRITICAL **: gnome_icon_selection_clear: assertion `gis != NULL' failed

(alacarte:8414): GnomeUI-CRITICAL **: gnome_icon_selection_add_directory: assertion `gis != NULL' failed

(alacarte:8414): GnomeUI-CRITICAL **: gnome_icon_selection_show_icons: assertion `gis != NULL' failed

I ignored this and continued the instalation, the Dofus is present in the games menu but when  I click it a window with a black background pops up for about a second then closes

---

### Post by Perfect Storm on 2007-05-06
The warnings is properly from the theme/icons you're using and is not related to the game.

Try run;
```
sh /home/**USERNAME**/.Games/Dofus/StartDofus.sh
```

What output do you get?

---

### Post by waggygee on 2007-05-06
it opened a page on firefox with a bunch of Dofus characters... in the top left corner it says 

Initializing DOFUS...
 Dofus version:1.18.1 build (4203)
Flash player (plugin) LNX 9,0,31,0

In the bottom left it says

[COLOR="Red"]Error: You must configure DOFUS as a trusted application on the flash player security settings
[/COLOR]
[COLOR="Red"]_Click here to see the solutions_[/COLOR]

When I click it nothing happens and I'm not sure where to find the flashplayer security settings. In the bottom right corner the is blinking writting that reads "Loading...."
Somehow I highly doubt that is happenin

---

### Post by Perfect Storm on 2007-05-06
If you can give me an hour or two I take a look at it, but as I recall it you have to give it permission/access before it works (perhaps I should add that), but I can't recall it as it been awhile I have played it.

---

### Post by conjur3r on 2007-05-06
i remember having to allow popups to get to the next stage of the flash settings.  It took me a while but once I realised that, it was quick.

---

### Post by waggygee on 2007-05-06
No change... I doubt it is actualy loading anything, I think mine is just showing that page

---

### Post by Ruthenium on 2007-05-06
If I remember correctly you have to go to 

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html)

and allow the folder where you installed dofus. I had to do that multiple times because it didn't work right the first time I tried.

---

### Post by Perfect Storm on 2007-05-06
Okay here we go;
[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html)
click the link and give Dofus access.

Go to Global security settings.
add location
browser folder
<ctrl>+<L>

Insert;
**~/.Games/Dofus**

Done.

---

### Post by Perfect Storm on 2007-05-06
The guide have been updated which contains now how to let flash get access.

Please feedback if it works/not works.

---

### Post by waggygee on 2007-05-06
Its still behaving in the same manner. How do I uninstall it ( I want to try reinstalling it again) maybe I made a mistake somewhere

---

### Post by Perfect Storm on 2007-05-06
```
cd ~/.Games
rm -rf Dofus
```

By the way you have to stop Dofus and rerun the game after the changes.

Edit again :P : Instead of ~/.Games/Dofus try to write the whole path instead in Flash Global Security

---

### Post by waggygee on 2007-05-06
OK!! I got it running!! I read through the instructions and carried what I could out manually, I discovered that not all the DOFUS documents were moved to the destination given for some reason. All I did was unzip the original folder on the desktop and move them to the correct destination (instucting the computer to replace folders that already existed there). But no when I attempt to login, it says "Server not found. Impossible to login"
It give me a link to support on that... but unfortunatly I dont know what firewall my Ubuntu has (if it has) or how or where to find all these settings to change.... Sorry for being a bother.

---

