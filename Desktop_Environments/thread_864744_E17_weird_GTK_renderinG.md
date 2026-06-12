---
title: "E17 weird GTK renderinG"
date: 2008-07-19
forum: Desktop Environments
---

### Post by dracule on 2008-07-19
ok, for some reason my lower case G inst workinG, but uppercase is :/

but firefox, and a whole bunch of other apps all have weird renderinG. it looks like when you dont have teh GTK enGine installed and try to use the theme. like windows 95 kinda. 

anyways, is there anyway to fix this? because i like it thus far (althouGh it is a little pokey (GhostinG of windows and stuff) i dont know if that can be fixed or not.

also... wtf is up with my G? the cursor blinks like i am hittinG a key but nothinG shows up when i type. :/

---

### Post by earlycj5 on 2008-07-20
> **dracule said:**
> ok, for some reason my lower case G inst workinG, but uppercase is :/

but firefox, and a whole bunch of other apps all have weird renderinG. it looks like when you dont have teh GTK enGine installed and try to use the theme. like windows 95 kinda. 

anyways, is there anyway to fix this? because i like it thus far (althouGh it is a little pokey (GhostinG of windows and stuff) i dont know if that can be fixed or not.

also... wtf is up with my G? the cursor blinks like i am hittinG a key but nothinG shows up when i type. :/

Install gtk-chtheme2 and set your theme that you want to use using that.

Quickest way to use it after install is hit "alt-esc" in e17 and type "gtk-" it'll bring it up in the list for you to choose.

It's because your .gtkrc preferences aren't being read.  Gnome has it's own .gtkrc file it reads from.  e17 reads a generic .gtkrc-2.0 file.

Lots of info if you search on changing fonts and icon themes in .gtkrc-2.0 on Google.

---

### Post by smartboyathome on 2008-07-21
> **dracule said:**
> ok, for some reason my lower case G inst workinG, but uppercase is :/

but firefox, and a whole bunch of other apps all have weird renderinG. it looks like when you dont have teh GTK enGine installed and try to use the theme. like windows 95 kinda. 

anyways, is there anyway to fix this? because i like it thus far (althouGh it is a little pokey (GhostinG of windows and stuff) i dont know if that can be fixed or not.

also... wtf is up with my G? the cursor blinks like i am hittinG a key but nothinG shows up when i type. :/

How did you install E17? Try typing this and restarting X.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

