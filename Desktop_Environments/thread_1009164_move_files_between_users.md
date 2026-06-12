---
title: "move files between users"
date: 2008-12-12
forum: Desktop Environments
---

### Post by cigtoxdoc on 2008-12-12
How do I set up File Browser so that I can move files back and forth between /home/dad/documents/ and /home/son/documents/ ?

dad, of course, has set himself up as system administrator.

OS = 8.10

---

### Post by Izek on 2008-12-12
If he's a "Root" then he can just copy the files over through the file manager as per normal. (Root is not the same as System Admin, I'm pretty sure of it.)

---

### Post by cigtoxdoc on 2008-12-12
But Ubuntu will not let you log in as root except in terminal mode.  I installed "file sharing", but File Browser will still NOT let me do what I want to do.

John

---

### Post by Rudy507 on 2008-12-12
```
gksudo nautilus
``` I believe is how you open the gui file browser as a super user. From here, you should just be able to copy and paste. 

Do you want to change file ownership too?

---

### Post by cigtoxdoc on 2008-12-20
Thank you for your help.  gksudo nautilus worked perfectly.  

This is great stuff, especially for those of us who have gotten use to working with a well-known proprietary OS; and on systems we administer ourselves; are used to moving files around at will.

Why isn't this a standard feature for Nautilus in Ubuntu?

How can nautilus be set up to do this every time I log on?

John

---

### Post by Izek on 2008-12-20
1.
```
gksudo gedit /usr/share/applications/nautilus-computer.desktop
```

replace nautilus on the Exec= line with gksudo nautilus. Save.

2.
```
gksudo gedit /usr/share/applications/nautilus-folder-handler.desktop
```

replace nautilus on the Exec= line with gksudo nautilus. Save.

Restart the session by doing CRTL+ALT+Backspace

It isn't a standard feature because that would be a security hole I believe, plus it's annoying when you have to type in your password every time you first open nautilus.

---

