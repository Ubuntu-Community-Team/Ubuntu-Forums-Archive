---
title: "Odd problem that says i'm not the &quot;owner&quot;"
date: 2009-01-05
forum: General Help
---

### Post by Atilliar on 2009-01-05
I downloaded a file and attempted to move it to a folder in the file system and it says that I cannot.  I opened the properties to the folder and went to the permissions tab and there is a message at the bottom of the window that says that i am not the owner so I cannot change the permissions.

I am the only user for this computer and it is not a server or anything.  How do I get it to recognize me as the owner?  I would appreciate the help.

---

### Post by gettinoriginal on 2009-01-05
Alt F2 will open a box, type in 
```
 gksudo nautilus 
```
this will open your file browser as root and you can change permissions, or just move the file.  But be careful, you can do harm to your system as root.  :o

---

### Post by bodhi.zazen on 2009-01-05
You should also read and understand Linux Permissions (rather then just ignoring them and running as root).

See :

[uhelp]community/FilePermissions[/uhelp]

[uwiki]RootSudo[/uwiki]

---

