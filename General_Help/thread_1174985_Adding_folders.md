---
title: "Adding folders"
date: 2009-05-31
forum: General Help
---

### Post by Cyberhog on 2009-05-31
Alright so I'm trying to download brushes to gimp, but I can't because well... when I look there is no brush folder for Gimp. I am not given the option to make a new folder and when I try and edit the permissions so that I can add new folders it says that I am not the owner so I can't change file permissions. The weird thing is that I am the owner. I mean I downloaded it myself and I am administrator, so Why am I not considered the owner?

any help would be nice.

Sorry if this is in the wrong section and if you can link me to where i can figure this out, that would be much appreciated. Thank you

---

### Post by bodhi.zazen on 2009-05-31
See [FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions")

I assume you need to use sudo to copy (or gksu nautilus).

---

### Post by ajgreeny on 2009-05-31
Where are you trying to make a new folder?  It is only possible as your own user in your /home folder.  The only way you can do it in any system folders is with ```
sudo mkdir /folder/path/name
```or by running nautilus as root ```
gksudo nautilus
```but be very careful if you do that; delete something you shouldn't and it can be "goodbye" to ubuntu.

---

### Post by bollix47 on 2009-05-31
Look for a hidden file in your home directory called .gimp-2.4.  There is a brushes folder there and that's where I would copy the files.

---

