---
title: "Gnome - Menus have disappeared"
date: 2006-12-10
forum: Desktop Environments
---

### Post by Vilhelmo on 2006-12-10
Hello! 
I have a bit of a problem, my menus have disappeared in gnome. (See screenshot below). I got the problem when a menu with program starters freezed, I tried to stop gnome-panels and hoped that the menus would come back and restart itself, but now they are just grey, as on the screenshot. Any ideas how I can do to get my menus back?

---

### Post by meng on 2006-12-10
Can you right click on the panel, Add to Panel..., Utilities, Main Menu?

---

### Post by Vilhelmo on 2006-12-10
no :(

---

### Post by bapoumba on 2006-12-10
Hi, did you **killall gnome-panel** ?
Does this happen with another user (you can add one with **sudo adduser <new_user>**) ? If not, the problem is within your user .conf files (.gnome*).

---

### Post by Vilhelmo on 2006-12-10
The menus looks normal with a new "test"-user so the problem seems to be in my users .conf files... I use gnome, but I can't find the .conf file. Can I copy the same file from another user to reset all configurations? Maybe there is a way to reset the gnome conf file?

---

### Post by bapoumba on 2006-12-11
In nautilus, you can see hiden files, the ones starting with "." > view > show hidden files or CTRL + H.

You can rename the .gnome* files (.gnome, .gnome_private, .gnome2, .gnome2_private) one by one and logout-login back into your session to see which one is messing up. A default .gnome* file will be re-created when you login. Then you will have to pin down where the problem is.

In these cases, the theme files are often involved. You could start with using the default Human theme in the regular user session.

May be check the .gonf* files too.

---

### Post by Vilhelmo on 2006-12-11
A friend of mine helped me on this one today (irl!). We solved the problem by deleting all(!) configuration files in my home folder, we simply removed all .* files. I know there probably is a better way but this worked. The theme is back to human and all settings were reset. I guess if anyone has a problem linked to their user-settings, the rough way to "reset" a user is to run, from a terminal: "rm -r .*" from the users home folder.

---

### Post by bapoumba on 2006-12-11
Wow, that was a little ... rough, as you said ;)
Renaming the files allows you to go back to the original conf if needed, and going back to Human default theme is always a good idea in that particular situation.

---

### Post by veloce on 2007-03-06
Thanks for this thread.  I just had the same problem - no idea how I caused it - found that renaming gnome2 fixed it.

---

