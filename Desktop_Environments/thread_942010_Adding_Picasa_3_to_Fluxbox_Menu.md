---
title: "Adding Picasa 3 to Fluxbox Menu"
date: 2008-10-08
forum: Desktop Environments
---

### Post by entikryst on 2008-10-08
I use fluxbox on top of ubuntu rather than the native gnome.  I like picasa alot but it wasn't added to the fluxbox menu. I have to run it through bash.
  I created a submenu called favorites for my most used programs in which i would like to add picasa.  Although i don't know where the program is stored.  Maybe Wine?  Any clues? Thanks!!

---

### Post by Patb on 2008-10-08
Enti, the ease of editing the menu and the fact that all menu items are in one file is a big plus for Fluxbox for me. 

To edit the menu and add Picasa, you can download and install Fluxconf (in the normal repositories) and run the program "fluxmenu".  That gives you a gui for editing the menu.  

A word of warning though.  The Fluxconf package, according to RedSquirrel, "is a separate project (not part of fluxbox), is old and buggy and is not maintained anymore".  The tool Fluxkeys which is part of it, has a difficult bug if you use it to edit your shortcut keys.  I have never had a problem editing the menu though. 

Alternatively, you can edit the menu file "by hand".  
```
gedit ~/.fluxbox/menu
```

Some discussion of all this and some discussion of how the edit the menu by hand, can be found in this thread.  [http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)

Hope this helps.  Let us know if you have problems. 

Cheers, Pat.

Edit PS: You might also want to look at this: [http://ubuntuforums.org/showpost.php?p=4578833&postcount=154](http://ubuntuforums.org/showpost.php?p=4578833&postcount=154)

---

### Post by entikryst on 2008-10-08
I already know how to edit the menu's I just wanted to know where the picasa program is installed in my file system so i can add it to my favorites menu.

---

### Post by Patb on 2008-10-08
Sorry, I misunderstood you.  In a terminal try:
```
sudo updatedb
locate picasa
```
Cheers, Pat.

---

### Post by entikryst on 2008-10-08
It was /usr/bin/picasa all along i feel stupid. Thanks. I ended up adding "[exec] (Picasa) {/usr/bin/picasa} </opt/google/picasa/3.0/desktop/picasa.xpm>" to my favorites submenu

---

