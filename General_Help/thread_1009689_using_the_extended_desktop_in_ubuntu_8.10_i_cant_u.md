---
title: "using the extended desktop in ubuntu 8.10 i cant use the visual effects"
date: 2008-12-12
forum: General Help
---

### Post by jarrah-95 on 2008-12-12
when i turned on the extended desktop (just moved the screens in the resulition preferences and it asked me if i wanted to use virtual resulition and i said yes) and now none of the visual effects work ccsm dosent do anything and emerald dosent work then in the appearances it just says that it couldn't enable the desktop effects anyone know why and what i can do to stop this

---

### Post by eternalnewbee on 2008-12-12
Doesn't this work?
Press **ALT-F2**, and enter ```
compiz --replace
```

---

### Post by overdrank on 2008-12-12
To add to eternalnewbee as was asked in your other thread " what is the model of the graphics card and some system specs" :)

---

### Post by jarrah-95 on 2008-12-13
the emerald --repalce dosent work it dosent do anything and it the terminal it just gets rid of the jarrah@jarrah-laptop:~$ 
and ccsm dosent do anything eather 
by the way what do you mean by this
> **overdrank said:**
> To add to eternalnewbee as was asked in your other thread " what is the model of the graphics card and some system specs" :)

---

### Post by eternalnewbee on 2008-12-13
> the emerald --repalce dosent work it dosent do anything and it the terminal it just gets rid of the jarrah@jarrah-laptop:~$
and ccsm dosent do anything eather
by the way what do you mean by this
Quote:
Originally Posted by overdrank View Post
To add to eternalnewbee as was asked in your other thread " what is the model of the graphics card and some system specs"
Did you try ```
compiz --replace
```
> what is the model of the graphics card and some system specs
Go to **Main Menu > System > Administration > Hardware Drivers** for that.
Other system specs:
These are mine:
[B]Ubuntu Release 8.10 (intrepid)
Kernel Linux 2.6.7-7
GNOME 2.24.1
AMD Athlon(tm) XP 899.219 MHz 256 KB
GeForce 7300 GT.[/B]
If you don't know how to find out, install an application called **SysInfo**.
You can add it from **Add/Remove**.

---

### Post by jarrah-95 on 2008-12-13
compiz --rplace dosent work eather its got something to do with what happened when i used extended desktop

---

### Post by jarrah-95 on 2008-12-13
my graphics card is (i dont know why thiis whould help as it was working before with the same cards) intel mobile 945gm/gms, 943/940gml express intergrated graphics controler

---

### Post by overdrank on 2008-12-13
> **jarrah-95 said:**
> my graphics card is (i dont know why thiis whould help as it was working before with the same cards) intel mobile 945gm/gms, 943/940gml express intergrated graphics controler

As is was working with Intrepid 8.10?
 Then it may have been a update that cause the issue. You may try and boot into recovery mode and use the xfix option to help with the graphics issue.

---

### Post by jarrah-95 on 2009-10-03
im using junty now and have had the same problem and managed to fix it by un installing and reinstalling compiz now it all works perfictaly

---

