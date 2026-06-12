---
title: "Looks of Controls"
date: 2006-10-18
forum: Desktop Environments
---

### Post by justin on 2006-10-18
After switching to pekwm, I found that all the controls(menus, buttons) on programs are very basic, grey, and ugly. Much different from what I had under gnome.

[Screenshot]("http://img101.imageshack.us/my.php?image=guiexih6.png")

Someone on irc suggested I'd do the following:

strace -o ff.debug firefox

then

grep gtkrc ff.debug

which output the following:

lstat64("/etc/gtk-2.0/gtkrc", 0xbf87fe9c) = -1 ENOENT (No such file or directory)
access("/etc/gtk-2.0/gtkrc.en_US", F_OK) = -1 ENOENT (No such file or directory)
access("/etc/gtk-2.0/gtkrc.en", F_OK)   = -1 ENOENT (No such file or directory)
lstat64("/home/justin/.gtkrc-2.0", 0xbf87fe9c) = -1 ENOENT (No such file or directory)
access("/home/justin/.gtkrc-2.0.en_US", F_OK) = -1 ENOENT (No such file or directory)
access("/home/justin/.gtkrc-2.0.en", F_OK) = -1 ENOENT (No such file or directory)
access("/home/justin/.themes/Raleigh/gtk-2.0/gtkrc", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/share/themes/Raleigh/gtk-2.0/gtkrc", F_OK) = 0
lstat64("/usr/share/themes/Raleigh/gtk-2.0/gtkrc", {st_mode=S_IFREG|0644, st_size=69, ...}) = 0
open("/usr/share/themes/Raleigh/gtk-2.0/gtkrc", O_RDONLY|O_LARGEFILE) = 9
access("/usr/share/themes/Raleigh/gtk-2.0/gtkrc.en_US", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/share/themes/Raleigh/gtk-2.0/gtkrc.en", F_OK) = -1 ENOENT (No such file or directory)
---------------------------------------------------

Any suggestions as to where I should go from here?

---

### Post by justin on 2006-12-05
*bump*

It's been two months, and still haven't found a solution. ](*,)

---

### Post by Shatrat on 2006-12-05
Have you tried installing different themes for pekwm?  
I've never used that wm and I doubt too many people have experience with it, so you might want to read more pekwm-specific sources.

---

### Post by justin on 2006-12-05
I have tried different themes. The themes themselves (window borders) look just like they should, but the problem I am having is with the controls, or maybe I should say decor, within these windows. I guess I am wondering if its possible to use clearlooks with pekwm without having to run gnome also. Unfortunately, there aren't very many good sources for pekwm information. I found one post about decor, but it didnt sound like the problem I am having. I really like this window manager, and don't want to switch because of this, but it really looks ugly. :(

---

### Post by justin on 2006-12-06
My mom always said I was a shmuck.

I used gtk-theme-switch2 to select a new gtk2 theme (clearlooks) and it worked perfectly. :-#

---

