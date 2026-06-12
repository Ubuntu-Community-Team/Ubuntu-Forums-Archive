---
title: "deleting custom emblems"
date: 2008-07-19
forum: Desktop Environments
---

### Post by travislagrone on 2008-07-19
I made some emblems under the edit -> backgrounds and emblems function, and now I'd like to delete them.  I can't even find the files on my computer.  How do I do this?

Travis

---

### Post by pauper on 2008-07-19
Default emblems are scattered all over /usr/share directory:
/usr/share/pixmaps/pidgin/emblems
/usr/share/pixmaps/nautilus
/usr/share/icons/.../.../emblems
/usr/share/f-spot/icons/hicolor/.../emblems

Custom ones could be here $HOME/.icons/.../.../emblems

To find all default emblems directories run:

```
sudo find / -name *emblems* | less
```

---

### Post by travislagrone on 2008-07-19
Thanks for the help!

I found them in the last place on the list:

/home/optimus/.icons/hicolor/48x48/emblems,

where optimus is my user name.



Travis

---

