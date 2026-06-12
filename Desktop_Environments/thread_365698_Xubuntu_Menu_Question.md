---
title: "Xubuntu Menu Question"
date: 2007-02-19
forum: Desktop Environments
---

### Post by cragmonkey on 2007-02-19
OK, i have used linux for a little while now but am very new to xubuntu. My question should be pretty easy for someone that has some experience with xubuntu. Actually, I have 2 questions...

1. How do I add an application to the xfce menu? for example: I have installed rdesktop and would like it to show up under the 'Network' sub-heading. Where is the conf file (or whatever type of file it is...) to edit and add a link to the menu? 

2. If I go out to [http://www.xfce-look.com](http://www.xfce-look.com) and find a them I like, I download the tarball but there is no way to point the user interface settings to the location of the file. How can I make the newly downloaded theme show up in the list of available user interface themes?

Thanks in advance for your help...

---

### Post by kerry_s on 2007-02-20
1. You can right click on the menu icon> edit menu or settings> desktop settings> behavior. If you want it in a paticular section that takes a little more work, you have to create a entry in /usr/share/applications. I've attached the file, unpack it and copy it to /usr/share/applications.(gksu thunar /)

2. Just create a folder for it in your home directory and unpack it in there.
Example:
.icons <- for icons and mouse themes
.themes <- for themes, both window themes and gtk2.0 themes go in there.

---

