---
title: "Setting icons and cursor."
date: 2009-06-18
forum: Desktop Environments
---

### Post by del_diablo on 2009-06-18
Lets start the problem. I need to change a few looks on my desktop, its ubuntu 9.04 running openbox and about all gnome packages is removed since it was bloat. So i am running Openbox.
So its about done being set up.

Problems:
*No way to set the cursor
*No icons after removing gnome
One of the problems is that there is absolutely no documentation on this subject, which makes it a pain. The config files is written mostly after arch linux wiki, since it somewhat covers it. 

This is a screenshot of what it looks like............
[IMG]http://handhelds.org/scap/port.11255.png[/IMG]

my ~/xdefaults
```
Xcursor.theme:	BlueIllusion2
Xcursor.size:	18
```
This one is suppose to controll the mouse cursor, which it did 2 second into getting the screen launched. Now its even more obsolute, an accident involved dragging in Slim caused this "strange" reveresed cursor to be set as default.
What its set to point at is this [http://xfce-look.org/content/show.php/BlueIllusion2?content=106643](http://xfce-look.org/content/show.php/BlueIllusion2?content=106643) ,quite the contrast to what is actually showing.
This leads me to belive Ubuntu uses some strange config files, which must be overrided or something. Which got no documentation :(

my ~/.gtkrc-2.0
```
# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/home/delly/.themes/Duster/gtk-2.0/gtkrc"
include "/home/delly/.gtkrc.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT

```
Points towards the mime file, and it works on getting my Duster theme to work. So this one works.

my ~/.gtkrc.mine
```

gtk-icon-theme-name = "FinalOrder"


```
This is suppose to set the icons, as the screenshot shows......... it does not work.........

Help?

---

### Post by del_diablo on 2009-06-19
*bump* I need help on this :(

Edit:  using dkpg-reconfigre -a changed the mouse cursor to a black one which atleast faced the correct way.

---

### Post by del_diablo on 2009-06-20
Update, i solved atleast a little more of the problem. By changing a few lines in the .mime file to something valid and dragging all icons from .themes to .icons and reading their readmes for checking what they was identifed as.

Still, the cursor problem remains............... Followed this [one]("http://fluxbox-wiki.org/index.php?title=Howto_setup_Xdefaults"), and it did not do a thing...... 
Running the command did not help a bit..........
```
xrdb -load ~/.Xdefaults
```

---

