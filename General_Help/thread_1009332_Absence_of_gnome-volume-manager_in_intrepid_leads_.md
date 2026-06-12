---
title: "Absence of gnome-volume-manager in intrepid leads to issues for user"
date: 2008-12-12
forum: General Help
---

### Post by QwUo173Hy on 2008-12-12
I inserted a blank CD and choose to open CD/DVD Creator. I selected "always perform this action" (or however it's phrased).

However, I realize now that most times I will be needing Brasero, not CD/DVD creator. But there is no way for me to remove this new default behaviour and I have to close the CD/DVD Creator dialog every time now.

In Hardy, there was a Removable Drives and Media preference but it's not present in Intrepid. Is there a way to fix this issue without having to install software from the repos? (gnome-volume-manager is available in the repos)

Thanks,
Jarlath

---

### Post by SPr on 2008-12-12
Open a terminal and enter
```

gconf-editor

```
Press Ctrl+F and search for volume-manager and/or for the name of the program you chose to open the blank CD.

---

### Post by kostkon on 2008-12-12
> **jarlath said:**
> I inserted a blank CD and choose to open CD/DVD Creator. I selected "always perform this action" (or however it's phrased).

However, I realize now that most times I will be needing Brasero, not CD/DVD creator. But there is no way for me to remove this new default behaviour and I have to close the CD/DVD Creator dialog every time now.

In Hardy, there was a Removable Drives and Media preference but it's not present in Intrepid. Is there a way to fix this issue without having to install software from the repos? (gnome-volume-manager is available in the repos)

Thanks,
Jarlath
Nevermind...

---

### Post by mc4man on 2008-12-12
Just go to file management -> media -> Other Media and change. (or add another app if you so choose.

If you haven't enabled file management in your preferences menu then you can thru edit menus or open nautilus (home folder) edit -> preferences -> media, ect.


Edit: with any removable media you can also hold down the shift button while inserting media to get a pop up allowing you to choose, switch, add.

---

### Post by QwUo173Hy on 2008-12-12
Thanks mc4man. The File Management dialog doesn't help here because it doesn't deal with blank media. But the Shift Key method worked great. Thanks.

---

### Post by mc4man on 2008-12-12
Are you sur? This is from hardy but the same exists in intrepid.

Otherwise run this and post for me

```
cat ~/.local/share/applications/mimeapps.list
```

---

### Post by QwUo173Hy on 2008-12-12
My apologies mc4man, you are correct. I never dropped down that menu (I had audioDVD in mine) but blank CD is there too so that works also. Thanks so much for your help.

---

