---
title: "System Settings Custom Launcher"
date: 2011-10-14
forum: Desktop Environments
---

### Post by EgoGratis on 2011-10-14
I was wondering how would i create custom launcher under System Settings -> System? 

Thanks!

---

### Post by crdlb on 2011-10-14
Unfortunately, the easiest way to do this is to copy the .desktop file for one of the existing apps from /usr/share/applications to ~/.local/share/applications . Rename the file and modify the Name, Exec, etc. fields. The MimeType= is the critical line AFAIK.

---

### Post by EgoGratis on 2011-10-15
Thanks for pointing me in the right direction, you were right i just had to create new .desktop file! The .desktop file has to be in /usr/share/applications it did not work in ~/.local/share/applications. I opened some .desktop files from other launchers in System Settings -> System and just flowed the examples!

Thanks!

---

