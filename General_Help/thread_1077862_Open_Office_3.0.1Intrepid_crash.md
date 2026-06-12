---
title: "Open Office 3.0.1/Intrepid crash"
date: 2009-02-22
forum: General Help
---

### Post by sports fan Matt on 2009-02-22
I upgraded to Open Office 3.0.1 on Intrepid and it crashed..has anyone else had this occur?  I used this thread [http://ubuntuforums.org/showthread.php?p=6639054#post6639054](http://ubuntuforums.org/showthread.php?p=6639054#post6639054) for the install.  "due to an unsuspecting error, open office crashed, all your files will be automatically saved" "the files will be recovered automatically"

Any Ideas?

---

### Post by sports fan Matt on 2009-02-22
i did more digging and OOO 3 is fine, but 3.0.1 has this issue...I wonder why

---

### Post by sports fan Matt on 2009-02-26
Any ideas why this could occur?

---

### Post by scouser73 on 2009-02-26
Hi, did you delete the previous version of OpenOffice, as the same thing happened to me so I completely wiped it using > sudo apt-get remove openoffice*.*

---

### Post by konqueror7 on 2009-02-26
you have to delete the .openoffice.org in your folder and just leave the .openoffice.org2 behind...

for more info, [here]("http://ubuntuforums.org/showthread.php?t=948294")..

---

### Post by sports fan Matt on 2009-02-28
So do I delete openoffice completely? And shall I rename the Openoffice 2?

Edit: I see the link but the directions are confusing

---

### Post by konqueror7 on 2009-02-28
nope, there are two hidden folders in your home directory...one is ".openoffice.org" and the other is ".openoffice.org2", delete ".openoffice.org"...in case you still have previous openoffice installed, type in the terminal,
```
sudo apt-get autoremove --purge openoffice*
```
in this way, you just need to do a clean install of openoffice3

---

### Post by sports fan Matt on 2009-02-28
Is there much diff between 3.0 and 3.0.1?

---

### Post by konqueror7 on 2009-03-01
in my installation, i didn't notice any big changes really, its only probably bug fixes...

---

