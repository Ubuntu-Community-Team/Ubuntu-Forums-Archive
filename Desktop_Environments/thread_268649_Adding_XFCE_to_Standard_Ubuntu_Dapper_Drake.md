---
title: "Adding XFCE to Standard Ubuntu Dapper Drake"
date: 2006-09-30
forum: Desktop Environments
---

### Post by mac57 on 2006-09-30
I have installed and am using Ubuntu Dapper Drake with its default Gnome desktop. I was interested in trying out XFCE without having to completely re-install Ubuntu via Xubuntu. I can see a huge number of XFCE related packages in the Synaptic repositories - is there an "all of XFCE" sort of selection I could make, install all the necessary packages, and then have XFCE and Gnome show up as session types on the GDM login screen? Thanks.

---

### Post by DirtDawg on 2006-09-30
Open a terminal and enter:
```
 sudo aptitude update 
```
Then:
```
 sudo aptitude install xfce4 
```

Then you can choose the xfce on login :KS

---

### Post by aysiu on 2006-09-30
If you want "all of XFCE," install Xubuntu: ```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

---

### Post by mac57 on 2006-09-30
Thanks, worked great! I am surprised overall by the fact that Gnome and XFCE load in about the same amount of time. I had always thought that Gnome was a slow behemoth like KDE - it turns out to be a lot more lithe than I expected, while XFCE is now getting larger and slower than it used to be. Still, both Gnome and XFCE load faster than KDE, which is important on older hardware. Thanks again!

---

