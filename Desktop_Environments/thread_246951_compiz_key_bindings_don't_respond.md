---
title: "compiz key bindings don't respond"
date: 2006-08-30
forum: Desktop Environments
---

### Post by diffkid on 2006-08-30
Hi,

I recently installed xgl/compiz on Dapper, and everything seems to be working okay on the display end. However, none of the default keyboard shortcuts will work. Looking in gconf-editor, I see that the shorcuts are indeed assigned to the commands (I do not however, see any keyboard bindings in the gset-compiz tool). I've tried changing the keyboard assignments, but nothing happens, no matter what I try, or which commands I try. Changing other properties in gconf-editor is not a problem.

Anyone else come across this issue?

Thanks,
diffkid

---

### Post by Takkie on 2006-08-30
I had the same problem for a while. Changing your keyboard layout (System > Preferences > Keyboard > Layouts) will probably do the trick.

Up till now I had to do this everytime I booted XGL/Compiz, but after removing the line ```
xmodmap /usr/share/xmodmap/xmodmap.us
``` from my startcompiz file everything works fine. The xmodmap line is meat to fix the shift-backspace bug but I don't seem to have any problems of whatsoever.

The only shortcut that doesn't work on my system is "film effect" (ctrl+alt+arrow down). Does anybody know how to fix that or isn't that feature available in the current Compiz release?

---

### Post by mobin on 2006-08-31
Yes the film effect works but it isn't set up by default. You need to set the 
key bindings under gconf.

apps->compiz->plugins->cube->allscreens->options>unfold_key
Set this to <Control><Alt>Down

Easier
------
Alternatively just type the following into a terminal:

gconftool-2 --set --type string /apps/compiz/plugins/cube/allscreens/options/unfold_key "<Control><Alt>Down"

---

### Post by diffkid on 2006-09-02
Everything is working fine since I removed the xmodmap line and set the film key. Thanks for your help!

---

### Post by macabro22 on 2007-06-23
Where's that startcompiz file? I can't seem to find it.

---

### Post by vertago1 on 2008-04-01
My understanding is the startcompiz file is a file some people add to the .kde/Autostart/ folder to run compiz when they login to KDE. I am having this same issue with the key bindings not working, but I haven't been able to resolve it by changing keyboard layouts. I am running kubuntu 7.10

---

