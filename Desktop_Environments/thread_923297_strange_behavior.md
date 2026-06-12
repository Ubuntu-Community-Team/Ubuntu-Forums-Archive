---
title: "strange behavior?"
date: 2008-09-18
forum: Desktop Environments
---

### Post by thamood on 2008-09-18
when ever i create or edit a file in ubuntu a new hidden file with the same name is created and saved, for example if i created a file named "file1" and then edit it with gedit a new file will be created with the name "file1~" and the new file will always be there? it wont be deleted after i finish editing?

i've noticed this for along time, can someone explain this for me..plz

thanx in advance...

---

### Post by mcduck on 2008-09-18
By default, Gedit creates a backup of files you are editing. You can disable that in Gedit's setings..

---

### Post by thamood on 2008-09-18
thanx man for the quick reply,,

one more question, plz

i want to edit /usr/share/applications/nautlis.desktop
but i can't access it though nautlis, and i tried opening nautlis in SU mode but still and i even tried showing the hidden files and still no luck.

the only way i can edit this file is through the terminal.

any ideas? coz i edited it before through nautlis, but now it' doesn't apear.

---

### Post by kerry_s on 2008-09-18
> **thamood said:**
> thanx man for the quick reply,,

one more question, plz

i want to edit /usr/share/applications/nautlis.desktop
but i can't access it though nautlis, and i tried opening nautlis in SU mode but still and i even tried showing the hidden files and still no luck.

the only way i can edit this file is through the terminal.

any ideas? coz i edited it before through nautlis, but now it' doesn't apear.

press alt+f2, type> gksudo gedit /usr/share/applications/nautlis.desktop

---

