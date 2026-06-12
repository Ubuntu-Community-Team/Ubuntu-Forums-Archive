---
title: "This is a new one for me: Help"
date: 2009-11-04
forum: Desktop Environments
---

### Post by duncan503 on 2009-11-04
):PHI here is my new problem. Now on my desktop there are all the folders that are also in my home folder. If I delete (Music folder) one on the desktop the same one(Music folder) in my home folder will be delete as well. I try to merge them but it will not allow it. So what is wrong with that, any idea.:mad:
Thank you for the help.
G

---

### Post by m4tic on 2009-11-04
what method did you use to get them to your desktop

---

### Post by duncan503 on 2009-11-04
> **m4tic said:**
> what method did you use to get them to your desktop

I have no idea . But I was on KDE environment for a while and try to set up KDE without success and got back with Gnome and that problem started.!

---

### Post by AgenT on 2009-11-04
GNOME (actually, Nautilus) has the option of using your home directory as your desktop. To switch:

Go to Applications -> System Tools -> Configuration Editor *

Go to apps, then nautilus, and click on the preferences folder.

Scroll down on the right side until you see the desktop_is_home_dir key and uncheck the box. (make sure to make a Desktop folder in your home directory before you do this if it does not exist)

* if you can't find it there, open the run menu (ALT+F2) and run this program: gconf-editor

---

### Post by duncan503 on 2009-11-04
Thanks I did what was written and no luck. the box in nautilus was uncheck .

---

### Post by duncan503 on 2009-11-05
Bumps

---

### Post by pjbgravely on 2009-11-06
Right click, properties on the desktop folders, If it says "type: link to folder you should be ok to delete it. Probably best to back up each folder somewhere else first.

If it is actually the file the take a screen shot and copy  the folders to a different name on your home directory, delete the folders, then rename the copied folders and add the emblem to copy what was in the screen shot.

Paul

---

