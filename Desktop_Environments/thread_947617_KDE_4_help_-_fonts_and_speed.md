---
title: "KDE 4 help - fonts and speed"
date: 2008-10-14
forum: Desktop Environments
---

### Post by laurence91 on 2008-10-14
Hi there, iv successfully been using KDE 3 on Kubuntu for some months and have very much enjoyed it, one problem is that the fonts on some applications home grown or science specific ones were low resolution and look pretty bad. So i decided to go for KDE4 thinking this would solve my problems, in actual fact all the fonts are now bad, even in firefox it actually hurts my eyes. Plus when i open firefox for example it takes ages and comes up with a small screen saying 'stating' first. If it helps i have a Dell XPS m1530 using kubuntu hardy, with KDE 4.1.

Please help before i lose my sight!

cheers
Laurence

---

### Post by benerivo on 2008-10-14
Beyond changing the font settings in 'kde4 system settings', the only other font management technique i know of is to run```
sudo dpkg-reconfigure fontconfig-config
```and then```
sudo dpkg-reconfigure fontconfig
```And log out and back in again. You'll have to answer about four questions on fonts, and remember the original settings if you want to change them back to default. Also, in kde4 system settings there is an option to force gtk applications such as firefox to use the kde4 fonts. Have you tried changing this?

---

### Post by laurence91 on 2008-10-15
hi, thanks, i worked out the fonts in the end it was todo with the aliasing. Although i have found an issue with my graphics card it doesnt seem to be working and thus is making the system slow. On KDE3 i used to be able to click on the battery and then select high performance i cant seem to do that in kde4.And does anyone know where to get the so called droid from?

Thanks

Laurence

---

