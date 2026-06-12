---
title: "Desktop icon removal"
date: 2008-05-28
forum: Desktop Environments
---

### Post by Big-B on 2008-05-28
I am getting my fingers around xubuntu, finally.  I'm trying it on one of the Eeepc's, the 2G surf model to be exact.  I loaded the OS onto the SD card with no problem, but since all the system partitions are on the SD card, it shows links to them on the desktop.  Is there an app or something I can edit into to stop them from coming up on the desktop?  I read someone mentioned gconf-editor, but that really hasn't worked to much as i'm not using nautilus.  any ideas?  Thanks!

---

### Post by mali2297 on 2008-05-28
From [here]("http://svn.xfce.org/svn/xfce/xfdesktop/branches/xfce_4_4/README"):
> 
The file icon view by default shows 'special' icons for the root of your
filesystem, your home directory, and the trash.  Removable volumes (such as
USB flash drives) are also shown when they are plugged in.  If you'd like to
configure which of these are shown, edit (or create) the file
~/.config/xfce4/desktop/xfdesktoprc to look something like this:

[file-icons]
show-filesystem=true
show-home=true
show-trash=true
show-removable=true

The defaults are all 'true', but you can set ones you want hidden to 'false'.
If an entry is omitted, it defaults to 'true'.  You will need to restart
xfdesktop to make the settings take effect.


You can try setting 'show-removable' to 'false'. Of course, that will hide all other removable volumes as well.

---

### Post by Big-B on 2008-05-29
Awesome, worked great.  Not bothered by it hiding all other volumes, i know where they are anyway!!  haha  thanks again.

---

