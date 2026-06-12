---
title: "Home directory icons appeared on Gnome desktop."
date: 2008-06-21
forum: Desktop Environments
---

### Post by David Haas on 2008-06-21
When I turned on my laptop running 7.10 with Gnome today, all the icons for the folders and files in my home directory appeared on the desktop--they looked the same as they look in Nautilus. I don't know how to get rid of them. I can't delete them, because this would delete their contents as it would in Nautilus. Anyone know how to eliminate these icons on the Gnome desktop?
David

---

### Post by angry_johnnie on 2008-06-22
If you open **/home/YOU/.config** there should be a file called **user-dirs.dirs**

Open it with a text editor, look for the DESKTOP line, and change it to this:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```


I'm pretty sure that should do it.

---

### Post by David Haas on 2008-06-23
I opened the .config file in my home directory, opened the file in it called user-dirs.dirs with Gedit, found the DESKTOP line and added to it /Desktop to give the line you suggested: XDG_DESKTOP_DIR="$HOME/Desktop". Then, I rebooted, but the same folder and file icons appeared. When I then re-checked the above altered line, I saw that it had been changed back to the default:  XDG_DESKTOP_DIR="$HOME".

Any other suggestions?

David Haas

---

### Post by cpetercarter on 2008-06-23
You did save the amended user-dirs.dirs before rebooting?

---

### Post by David Haas on 2008-06-23
Yes, I did save the change made to the line. Although this didn't work, I found out elsewhere in this forum how to delete all the Home-directory icons from the desktop: I typed gconf-editor in the terminal to open the graphical Nautilus Configuration Editor. In this, I scrolled down to the "nautilus" folder, opened it, and selected the "preferences" folder. In this is a file called "show_desktop". Its value box was checked (meaning the command was on). I unchecked it, and all the icons vanished! How this came to be on is beyond me.

Thanks for trying to help me solve this problem.

David Haas

---

### Post by RodGer GR on 2009-11-24
But... unchecking the "show_desktop" option just vanishes all the desktop icons. I have the same problem and no matter what I do, I can't change the path for the Destop folder from /home/rodger to /home/rodger/Desktop.

Is there any other way to fix this? I would file a bug but I don't know how to reproduce it :-|

---

