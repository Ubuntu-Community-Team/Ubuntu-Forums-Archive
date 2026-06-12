---
title: "No write permission"
date: 2004-11-28
forum: Desktop Environments
---

### Post by peter_barb on 2004-11-28
Well, I dowloaded a theme and icon package. I want to move it to the /usr/share/icons, and usr/share/themes. Just everytime I drag and drop the directory it says "Permission denied". How do I get rid of this? Would I need to login with root through the terminal?

If so, what would I need to type into terminal?

Thanks,
Peter
[http://peterbarbosa.com](http://peterbarbosa.com)

---

### Post by Marauder1 on 2004-11-28
Dont have to move these files,
just when you need them, make a file
browse to your home directory and pick them.

---

### Post by peter_barb on 2004-11-28
Well its just like once I dowloaded skype. I need to move these files over, and it won't let me because it says I do not have permission..

How do I do this?

---

### Post by HungSquirrel on 2004-11-28
To drag and drop files where you need root permission to do so, click Applications -> Run Application... and type *gksudo nautilus* to open a file browser as root.  It will ask you for your user password, then a file browser window will launch.

---

### Post by ulrich on 2004-11-28
do you really need to move this packages?
you can simply do an

computer > desktop-prefs > themes 

and install/choose this themes.
even if this wont work, themes go in the /home/YourUserName/.themes folder.

---

