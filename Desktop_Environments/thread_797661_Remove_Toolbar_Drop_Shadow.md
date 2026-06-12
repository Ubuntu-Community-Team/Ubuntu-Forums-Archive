---
title: "Remove Toolbar Drop Shadow"
date: 2008-05-17
forum: Desktop Environments
---

### Post by UniverseA7X on 2008-05-17
I want to make my toolbar completely transparent to blend in with the background, but it has that drop shadow no matter what. can i remove this? I had it perfect in KDE, but I've seen some pictures of Gnome without this shadow on the bar. Thanks

Brandon

---

### Post by chewearn on 2008-05-18
If you have done so, install CCSM.

Click this link:
[apt://compizconfig-settings-manager](apt://compizconfig-settings-manager)

Or, run this command:
```
sudo apt-get install compizconfig-settings-manager
```


Then, open CCSM:
System > Preferences > Advanced Desktop Effects Settings

Select Window Decoration plugin (under Effects).  in the last line "Shadow windows", change "any" to "(any) & !(class=Gnome-panel)".

.

---

### Post by Jordinho on 2008-05-19
Worked for me.

---

### Post by aroch1 on 2008-05-20
That's exactly what I do to get rid of my shadows.

---

### Post by broken tibula on 2008-08-26
Thanks!  This was jsut what I was looking for, too!

---

### Post by digitalmusic on 2008-08-26
Thanks for that - worked for me too.

---

### Post by thikidflyss on 2009-03-16
thanks this worked

---

