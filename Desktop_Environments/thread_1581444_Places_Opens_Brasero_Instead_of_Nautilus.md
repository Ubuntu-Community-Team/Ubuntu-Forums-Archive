---
title: "Places Opens Brasero Instead of Nautilus?"
date: 2010-09-24
forum: Desktop Environments
---

### Post by linux4me on 2010-09-24
I just backed up a 8.04 installation's home directory, did a clean install of 10.04 from the alternate CD, then restored the old home directory. 

Everything seems to be working fine except for one thing. When I click on a link in the Places menu (Desktop, user folder, etc) Brasero opens instead of Nautilus!

I've searched and haven't found any explanation for this. I've also looked through gconf-editor and can't find a setting that would explain it. In gconf-editor desktop -> gnome -> applications -> component viewer is set to "nautilus %s."

I tried running:```
sudo dpkg-reconfigure nautilus
```but that didn't help.

How in the world do I get Nautilus to be the default application for the folders in Places?

---

### Post by Rasa1111 on 2010-09-24
heya, same happened to me when i installed 10.10. 

 To fix it,
you just right click on a folder, hit "open with other application"..
and then choose "open folder"..
 and check, "remember this application for folder files" at bottom. 

 That is the temp fix i guess, anyway..
Someone else here told me. 

 Works great here now though, after doing that. 

 I actually had to go into "computer",
and right click on a folder from there. 

g'luck.

---

### Post by Rasa1111 on 2010-09-25
[http://ubuntuforums.org/showpost.php?p=9870576&postcount=5](http://ubuntuforums.org/showpost.php?p=9870576&postcount=5)  :)

---

### Post by linux4me on 2010-09-25
> **Rasa1111 said:**
> heya, same happened to me when i installed 10.10. 

 To fix it,
you just right click on a folder, hit "open with other application"..
and then choose "open folder"..
 and check, "remember this application for folder files" at bottom. 

 That is the temp fix i guess, anyway..
Someone else here told me. 

 Works great here now though, after doing that. 

 I actually had to go into "computer",
and right click on a folder from there. 

g'luck.

Thanks for the quick reply, but that didn't work. I tried going into Computer in Nautilus, right clicked on "file system" and chose "open folder." No joy. Brasero still opens. Then I tried going into Computer, browsing to the "home" folder, and tried the "open folder" thing with "open with other application" but Brasero still opens! :confused:

---

### Post by linux4me on 2010-09-25
I finally figured this out with the help of [this bug report]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492").

Apparently, the problem file was /home/ <user>/ .local/ share/ applications/ mimeapps.list:
> [Added Associations]
application/x-compressed-tar=f-spot-import.desktop;
application/x-gzip=f-spot-import.desktop;
inode/directory=brasero.desktop;nautilus-cd-burner-open-iso.desktop;nautilus-folder-handler.desktop;nautilus-browser.desktop;userapp-nautilus-S9U5IV.desktop;
application/x-extension-link=nautilus-folder-handler.desktop;
x-content/software=nautilus-autorun-software.desktop;
If you look at the "inode/directory" line, brasero.desktop is first in line. I think some of the subsequent entries are due to my attempts to add "open with other application" entries.

This file obviously got moved over when I restored the old home directory for the machine. Renaming the file--or deleting it--is a fix, as would be changing the inode/directory line to include just "nautilus-folder-handler.desktop". 

Since there aren't that many files in the backup, I'm going to do another install and just copy over the files and folders I know I need so there aren't any more gotchas like this one down the line.

---

### Post by darkwing_duck on 2011-01-05
I changed the inode line to the following:

```
inode/directory=nautilus-folder-handler.desktop;
```


Works so far. Thanks for the solution!

---

### Post by Pratik Ali on 2011-04-10
Yes, the mimeapps.list solution works for me too (10.10)!

---

