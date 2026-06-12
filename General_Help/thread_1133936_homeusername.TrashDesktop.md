---
title: "/home/username/.Trash/Desktop"
date: 2009-04-23
forum: General Help
---

### Post by adit on 2009-04-23
I incidentally deleted all the files in my home folder.  Now whatever new folder I create in the Desktop it is not created in **/home/username/Desktop**. It is actually created in **/home/username/.Trash/Desktop**.  I want to restore to previous Desktop. What to do?

---

### Post by John Cheng on 2009-04-23
Maybe try using a file manager (Dolphin or Gnome File Browser) to rename your current /home/username/Desktop to /home/username/Desktop.backup and then move /home/username/.Trash/Desktop to /home/username/Desktop?

---

### Post by adit on 2009-04-23
> rename your current /home/username/Desktop to /home/username/Desktop.backup and then move /home/username/.Trash/Desktop to /home/username/Desktop?
I did what you said.  Now whenever I try to create a new folder in desktop a dialog box appears.
"Error "File not found" creating new folder"

---

### Post by John Cheng on 2009-04-23
Strange, do you use Gnome or KDE? It seems that the system is still looking at /home/username/.Trash/Desktop as your "desktop" folder.

Did a little googling and found one possible way it could've happened:

[http://freedesktop.org/wiki/Software/xdg-user-dirs](http://freedesktop.org/wiki/Software/xdg-user-dirs)

Does this sound familiar to you?

Or you might try toggling the "desktop_is_home_dir" value if you are using Gnome (described here), but I'd say back up your home directory before trying this.

[http://ubuntuforums.org/showthread.php?t=341607](http://ubuntuforums.org/showthread.php?t=341607)

---

### Post by adit on 2009-04-24
I edited the file /home/username/.config/user-dirs.dirs. I changed the entry
XDG_DESKTOP_DIR="$HOME/.Trash/Desktop" into
XDG_DESKTOP_DIR="$HOME/Desktop"

Problem solved.  Thank you John Cheng.

---

