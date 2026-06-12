---
title: "i cannot install themes!!"
date: 2009-03-23
forum: Desktop Environments
---

### Post by Rockanium on 2009-03-23
i cannot install themes!!
i try to drag the file into the themes folder
/usr/share/themes

but it says:
Error while moving "icknessblack".
There was an error moving the file into /usr/share/themes.
Error moving file: Permission denied

why does it say premission denied?

p.s i am a linux noob

---

### Post by null.byte on 2009-03-23
You need root permissions.

---

### Post by Rockanium on 2009-03-23
Okay, How do i do that?

---

### Post by mcduck on 2009-03-23
You can install the them from command line, using "sudo" with the commands to run them with root privileges.

..or do it from the GUI, by running the file manager with rot permissions. To do that press Alt-F2 and run "gksudo nautilus". Be sure to close the window when you are done..

But unless you really want/need to install the theme system-wide you could just install it for your own user instead. To do that just extract the theme to .themes directory inside your user's home. Or open System/Preferences/Appearance and drop the theme package to the window to install it.

edit: you should probably read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

