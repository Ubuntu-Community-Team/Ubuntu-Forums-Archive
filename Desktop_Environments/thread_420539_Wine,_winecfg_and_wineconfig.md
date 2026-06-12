---
title: "Wine, winecfg and wineconfig"
date: 2007-04-23
forum: Desktop Environments
---

### Post by SRTS on 2007-04-23
I installed wine and noticed there are two different configtools, called "winecfg" and "wineconfig". Is one of them bad or old or why are there 2 different tools? They also differ slightly in the options they have available.
Wineconfig seems to look "newer" but it generates lots of errors mentioning some .regedit.rc stuff each time I run it.

---

### Post by stbub on 2007-04-23
> **SRTS said:**
> I installed wine and noticed there are two different configtools, called "winecfg" and "wineconfig". Is one of them bad or old or why are there 2 different tools? They also differ slightly in the options they have available.
Wineconfig seems to look "newer" but it generates lots of errors mentioning some .regedit.rc stuff each time I run it.

I only see winecfg on my system (ubuntu 7.04)

---

### Post by loyeyoung on 2007-06-20
winecfg is a wine program that works something like control panel, from within the simulated Windows environment. 

wineconfig is a python script running as a part of KDE Guidance that changes various settings that Wine uses. 

They do have some overlapping functionality. However, wineconfig can do things that winecfg cannot, like read your desktop color theme settings and make wine conform so that it's not as ugly. 

If you are running the Gnome desktop (i.e., you are running the Ubuntu desktop, not Kubuntu), you don't have wineconfig.

Loye Young
[http://www.iycc.biz](http://www.iycc.biz)
Laredo, Texas

---

