---
title: "HOW-TO: install themes, icons, and cursors."
date: 2009-01-17
forum: General Help
---

### Post by Wartender on 2009-01-17
ok so this is my first "howto" thread, and since i've seen so many threads of people asking how to do this, i've decided to try and write a little guide to help anyone with these problems.

getting your icons, themes, cursors:

now there are many places to get these things, my favorite is [www.gnome-look.org](www.gnome-look.org), along with all the other -look.org websites. 

installing them:
ok so here is how to install icons, themes, and cursors in a few different ways (just in case one doesn't work for you)

ICONS:
the basic way is to open appearance (system->preferences->appearance, and drag your downloaded tarball (.tar.gz or.tar.bz2 or anything with .tar) onto the main window of appearance make sure to drag the tarball, DO NOT extract the folder then drag the extracted folder, this will not work. after dragging you are given the option to use it immediately or not, choose whatever you want. to change them click on the theme you are using and click customize and the icons tab to change your icons

another way is to go to your home directory (/home/YOURUSERNAME) remember to substitute YOURUSERNAME with... well... your user name. here you press ctrl+h to show the hidden folders you need. go to .icons and copy the EXTRACTED folder (unlike the first method now you HAVE to extract the folder) into your .icons directory. then open appearance and click customize and under the icons tab select your icon theme.

CURSORS:
installing cursors is almost identical to installing icons, everything is the same except when you want to change them you go to the pointers tab instead of the icons tab. everything else is exactly the same (yes cursors are in the .icons directory too)

GTK THEMES:
gtk themes are almost the same as well, except that when you want to change them, you don't hit customize, the list of installed themes is there already (in appearance) and the folder they reside in is .themes, not .icons, the instructions for installing are the same.

EMERALD THEMES:
if you have emerald installed (you can get it from synaptic (system->administration->synaptic package manager) by searching emerald) then the installation is the same as the one for GTK themes, except you drag the tarball onto the emerald themer main window, not the appearance one.
to install the second way go to your home again, press ctrl+h again, and go to the .emerald/themes folder, there you can drag the extracted folder

after installing themes in emerald and setting them up remember to go into a terminal and type emerald --replace to make emerald the window decorator, otherwise the themes won't appear.

and there you go, this is pretty much all you need to know when installing themes, icons, or cursors. thanks for reading and happy customizing, if you have any questions please post them. :)

---

### Post by Briped on 2009-01-18
**Confessions of a total eyecandy noob**

First of all, thanks for taking the time to make a howto for someone like me.
I downloaded this nice theme to my desktop - the file is called somethingorother.tar.gz. At least I believe it's a theme, but I'm so noob that I'm not even sure what the difference between 'a theme' and 'a wallpaper' is. Anyway, when I look inside the file it contains more than just a *.png file, and assuming that a theme is wallpaper + icons (and more?), I saved it in my /home/username/themes folder, right clicked on it and chose 'extract here'. I opened 'appearance preferences' and in themes I clicked 'install' and navigated to my extracted theme. My file was now called 97732-somethingorother (no tar.gz), and not .theme-somethingorother like the other theme already present in the folder. I clicked to highlight it, then 'open' - but this just opened it like a folder that looks empty.
I'm sure I've either misunderstood - or not understood at all, your choice ;) I don't know if you can shed some light on this?
I run Intrepid Ibex. No desktop effects (yet)

Kind regards,
Britta, who feels a little too noob right now, but knows she'll keep feeling noob if she doesn't ask.

---

### Post by Martje_001 on 2009-01-18
Maby you should post it in Tutorials & Tips? Or ask a mod.

---

### Post by Wartender on 2009-01-19
Briped, can you tell me where exactly you got the theme? and have you tried dragging the .tar.gz file onto the main window of appearance? (system->preferences-> appearance)

edit:
oh and to Martje_001: i never even noticed there was a tutorials & tips forum... in that case what i wrote is probably there already, i didn't find it in this section so i guess that's why i felt like i should write one... oh well i'll just leave this here and see if it helps anyone else

---

### Post by Briped on 2009-01-21
Hi Wartender,
I got the theme here: [http://gnome-look.org/content/show.php/Homero+Eats+Vista?content=97038](http://gnome-look.org/content/show.php/Homero+Eats+Vista?content=97038). I also tried installing it by dragging the file into the main screen of appearance preferences --> theme tab, but got the error message 'this file does not appear to be a valid file'.

Kind regards,
Briped

---

