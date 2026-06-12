---
title: "Volumes in Xfce (Xubuntu Feisty)"
date: 2007-04-28
forum: Desktop Environments
---

### Post by bikmak on 2007-04-28
Hi!

In Xubuntu I realized that the are my hard drives in the desktop (and thunar's side pane) automaticly. It's good, but I have a little problem, the name of these are 78G volume, 38G volume, etc. How could I rename these for a little more readable names?

---

### Post by aidanr on 2007-04-28
well one way to do it would be to modify /etc/fstab to mount them somewhere like /mnt/bettername/ and then recreate the shortcuts on the desktop and in thunar

---

### Post by bikmak on 2007-04-29
they are in /media/data1 and data2 but despite of this have they these horrible names. 
I created shortcuts in thunar's sidepane, but its not the perfect solution, because they are duplicated, and its engage "usefull" room.

[ Otherwise in Gnome there isn't this problem, so I think it's only Xfce's / Thunar's miss, not (X)ubuntu. ]

---

### Post by aidanr on 2007-04-29
if you mount them outside of media (for example /mnt) they won't show up as 78G volume etc

---

### Post by bikmak on 2007-05-01
I see. Thx!

---

