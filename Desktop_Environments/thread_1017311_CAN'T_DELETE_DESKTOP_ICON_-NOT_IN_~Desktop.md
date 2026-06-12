---
title: "CAN'T DELETE DESKTOP ICON -NOT IN ~/Desktop?"
date: 2008-12-20
forum: Desktop Environments
---

### Post by linuxisevolution on 2008-12-20
I want to clean up my desktop. I have four icons LOL but it buggs me so i moved them to the taskbar. ( icons are Computer, 124gb media , Home, server )

I want to delete Home and Computer, but when clicking on the icon and pressing delete I get the attached image. **NO FILES ARE IN /HOME/WINRID/Desktop**. I am confused. sudo rm -i ~/Desktop/Home does nothing. find /home/winrid/Desktop reports nothing. If these icons do not exist, were in the hell are they?

---

### Post by xjcannonx on 2008-12-20
Try going into your gconf-editor by hitting alt-F2-->gconf-editor

Then go to apps-->nautilus-->Desktop

There should be an option to hide or show your computer and home folder

---

### Post by linuxisevolution on 2008-12-20
> **xjcannonx said:**
> Try going into your gconf-editor by hitting alt-F2-->gconf-editor

Then go to apps-->nautilus-->Desktop

There should be an option to hide or show your computer and home folder

Thank you sooooo much! It works, but, where were these file's located to begin with?

---

### Post by xjcannonx on 2008-12-20
Not sure, my guess is that it creates some sort of symlink on your desktop...

---

### Post by Ng Oon-Ee on 2008-12-21
Those aren't 'files' per se, if you browse to your Desktop using Nautilus I don't believe you'll see them. What's shown on your desktop are any files you've placed there as well as some launchers (such as 'home' and your mounted drives).

This is slightly different from Windows, which just places shortcuts to everything on the Desktop.

---

### Post by linuxisevolution on 2008-12-21
Thanks. But were is the setting for this stored, ( text file ). I love the concept of everything in Unix being a text file.

---

### Post by xjcannonx on 2008-12-22
/home/username/.gconf/apps/nautilus/desktop/%gconf.xml

This is the xml file for what you were wondering

---

