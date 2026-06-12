---
title: "Icon and files missing on desktop"
date: 2008-02-04
forum: Desktop Environments
---

### Post by kaziklcd on 2008-02-04
Hello to all :D

My problem is as follow:
- I tried to remove some *.rar file from Desktop, right after that my Desktop blinks and all files and folder just disappeared.
I try this ```
apt-get install xfce* --reinstall
``` but no success. I found interesting file name **icons.screen0.rc** in ~/home/woda/.config/xfce4/desktop location, with complete list of my lost desktop files and folders 
```
[Od&#380;ywki.ods]
row=0
col=0

[karta klienta.odt]
row=0
col=8

[rozliczka.ods]
row=4
col=0

[Rozliczenie2007.xls]
row=6
col=2

[System plików]
row=4
col=0

[Katalog Domowy]
row=3
col=0

``` but no files or folder that names on Desktop :(

Ill be appreciate for any help. 

I using
XFCE 4.4
PCMan 0.3.2.2
Gutsy Gibbon

---

### Post by Foxray on 2008-02-04
You may have accidentally turned off desktop icons on xfce. Check in Desktop Settings on the 2nd tab the pull down box says Use Desktop Icons and not None. Removing a rar file on the desktop should not delete everything.

---

### Post by kaziklcd on 2008-02-04
it was one of my first check :)

---

