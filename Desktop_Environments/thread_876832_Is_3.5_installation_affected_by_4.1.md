---
title: "Is 3.5 installation affected by 4.1?"
date: 2008-08-01
forum: Desktop Environments
---

### Post by dijxtra on 2008-08-01
I'm sorry if this matter was already discussed, but I coudn't find anything about this by searching. I have KDE 3.5 and would like to try KDE 4.1, but it is **very** important to me that my 3.5 installation is not affected in any way. Can I be like 95% sure that if I install KDE 4.1 and login to KDE 3.5 everything will be as it used to be defore I installed KDE 4.1?

Regards,
dijxtra

---

### Post by der_joachim on 2008-08-01
Your kde3 installation will be unaffected. The same goes for your local settings. KDE3 stores all of its settings in the .kde subdirectory in your ~. KDE4 will save them in ~/.kde4 .

---

### Post by mortenb on 2008-08-01
der_joachim is corrent. I just installed kde4.1 alongside my kde3.5.9 and nothing in the 3.5.9 was changed.

---

### Post by dijxtra on 2008-08-03
Hm. After installing KDE 4.1 my KDE 3 K-menu got unusable. It's overcrowded with KDE 4 apps, many of those duplicates of KDE 3 apps. The thing is that I migrated from gnome to kde (I used ubuntu, and then installed kubuntu-desktop) because I liked KDE but wanted to be able use some gnome apps. So, in my KDE menu I had KDE 3 apps and gnome apps. And now I have, KDE 3, gnome and KDE 4 apps. So the menu is pretty much overcrowded to the point of being unusable.

So, to rephrase my question from the first post: can I have two nonoverlaping installations of KDE 3 and KDE 4? I would like to have KDE 3 with my KDE 3 and gnome apps, and KDE 4 with KDE 4 apps. Is that possible without making two distinct operating systems (i.e. two partitions, two grub entries, etc.)?

If KDE 3 and KDE 4 must overlap, is there a way to remove KDE 4 without removing KDE 3? I found a piece of advice in [this thread]("http://ubuntuforums.org/showthread.php?t=874818"):

```
sudo aptitude purge kubuntu-kde4-desktop
sudo aptitude purge kdm-kde4
sudo dpkg-reconfigure kdm
sudo aptitude purge ~nkde4
```

I'm not a novice GNU/Linux user, and to me it looks like this code will remove only KDE 4. But I'm not that proficient either, so I would appreciate if somebody would reaffirm my opinion that this code will only remove KDE 4.1.

Thanks in advance.

---

