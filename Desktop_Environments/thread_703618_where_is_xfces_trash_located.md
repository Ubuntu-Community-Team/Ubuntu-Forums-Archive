---
title: "where is xfces trash located?"
date: 2008-02-21
forum: Desktop Environments
---

### Post by KhaaL on 2008-02-21
can anyone tell me where xfce stores the trash? its not under ~/.trash and iäve tried to google the answer with no luck...

---

### Post by sisco311 on 2008-02-21
~/.local/share/Trash/files/

---

### Post by banewman on 2008-02-21
You should have a .Trash-username in your home folder.
Try in a terminal -
sudo updatedb && locate Trash
Make sure you type Trash with a capital T
:)

---

### Post by KhaaL on 2008-02-21
Thank you both. locating Trash showed it to be hiding under /home/khaal/.local/share/Trash
:)

---

