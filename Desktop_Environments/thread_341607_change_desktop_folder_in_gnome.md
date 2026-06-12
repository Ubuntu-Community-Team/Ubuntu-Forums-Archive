---
title: "change desktop folder in gnome"
date: 2007-01-18
forum: Desktop Environments
---

### Post by freeatlast? on 2007-01-18
hi

i would like to change the Desktop folder in gnome from the ugly ~/Desktop to something else (i have my home directory laid out all custom like). is this possible? i don't want a link in there, i don't want anything visible - there must be a setting somewhere, but i just can't find the damn thing. in fact, i don't seem to be able to find any of the "advanced" settings for gnome, only the basic stuff in gnome-control-center.

thanks for any and all help
cheers

---

### Post by ciscosurfer on 2007-01-19
> **freeatlast? said:**
> hi

i would like to change the Desktop folder in gnome from the ugly ~/Desktop to something else (i have my home directory laid out all custom like). is this possible? i don't want a link in there, i don't want anything visible - there must be a setting somewhere, but i just can't find the damn thing. in fact, i don't seem to be able to find any of the "advanced" settings for gnome, only the basic stuff in gnome-control-center.

thanks for any and all help
cheersCan you clarify exactly what you want to do...I'm a little confused by your first post.  You want your actual Desktop to be your Home directory (because you can do that)...but please explain this further as I may be misreading your post.

---

### Post by mcduck on 2007-01-19
if you don't want to see the Desktop directory inside your home dir you can create a file called .hidden inside your home dir, and add 'Desktop' on the first line of that file.

Actually you can hide anything you want that way, just create the .hidden file in the directory where you want to hide things and then add all files/directories to that file, each one on their own line.

edit: all advanced configuration in Gnome is done either with Configuration Editor (run 'gconf-editor') or by editing text files.

---

### Post by freeatlast? on 2007-01-19
thanks for the responses - i want to point my gnome desktop folder (the one that dictates what appears on my desktop) at a file system path of my choosing.

with the ,hidden tip (thanks, i didn't know that one), i can now simulate what i wanted to do by making ~/Desktop a link to my chosen path and hiding ~/Desktop with the .hidden mechanism. charming, ta very much. but this seems somewhat inelegant. do i _have_ to hack my way round this basic setting? anyone know how to do this _properly_ (tongue firmly in cheek there)? :D

in any case, my problem is effectively solved by that so thanks again.

---

### Post by mrc.gran on 2007-01-21
to change it to your homedir:
1) open gconf-editor
2) browse to /apps/nautilus/preferences entry in it
3) set desktop_is_home_dir flag

---

### Post by viniciusandre on 2007-12-24
you can also change the value for XDG_DESKTOP_DIR if in Gutsy using XDG.

Look for the file:
```
~/.config/user-dirs.dirs
```

In the following line:
```
XDG_DESKTOP_DIR="$HOME/"
```

Hope it helps...

---

### Post by skogsjanne on 2008-07-20
Thank you!

---

