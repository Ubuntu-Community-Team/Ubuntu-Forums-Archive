---
title: "multiple desktop environments"
date: 2010-08-12
forum: Desktop Environments
---

### Post by jistanidiot on 2010-08-12
So i'm using kubuntu 10.04 with KDE 4.4.  Having decided that KDE 4 is yet for me, I want to try out the just released 4.5 yet still keep 4.4.  I also want to try out xfce without destroying the two KDEs.

Are there any instructions for installing multiple desktop environments under kubuntu?  Is there some simple way of doing this?

---

### Post by 3Miro on 2010-08-12
To install XFCE you need to type in konsole:
```
sudo apt-get install xfce4
```
this will come with default XFCE4. You can also do
```
sudo apt-get install xubuntu-desktop
```
which will install xfce4 with xubuntu defaults and also change boot screen. To get a good xfce experience, you should also probably install:
```
sudo apt-get install xfce4-goodies
```
Then you can logout and login into xfce.

I don't think it is possible to get both KDE 4.4 and 4.5 on the same system, however, I may be wrong.

---

