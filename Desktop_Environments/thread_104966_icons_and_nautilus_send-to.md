---
title: "icons and nautilus send-to"
date: 2005-12-17
forum: Desktop Environments
---

### Post by paul555 on 2005-12-17
Hi all i want to ask about two things for gnome.First is it possible for a specific file type (for example *.doc) to assign a given by me icon?Second is there a way in nautilus when i right click a folder or a file to copy or cut it to an another location?

---

### Post by Sutekh on 2005-12-18
_Changing Icons _

You can assign an icon of your choice or design to a specific filetype.  

Installed icon themes will be in */home/user/.icons/<name of theme>*.
  
Then there will probably be folders for different sizes of icons; *.../64x64*, *.../128x128* and so on.  

The icons for filetypes are in the *.../mimetype* folder.  

Just replace the icon for the filetype with your own, by renaming your icon to that of the one you are replacing.  

The icon for .doc files will probably be called something like *gnome-mime-application-msword.png*, just copy and paste it, Nautilus will append *copy* to it (good in case you want to change it back), then rename your icon.



_Copy and Move To Nautilus Scripts_

This thread has a lot of scripts for Nautilus, the first post has the copy/move script.

[Link - Helpful Nautilus Scripts]("http://www.ubuntuforums.org/showthread.php?t=101870&highlight=nautilus+scripts")

---

### Post by paul555 on 2005-12-19
Thank you very much for your reply.It helped me a lot.For the icons if i want to assign an icon for a filetype of *.chm files that it isn't in /mimetype folder is there a way to do it?

---

