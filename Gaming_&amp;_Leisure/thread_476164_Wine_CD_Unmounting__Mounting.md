---
title: "Wine CD Unmounting \ Mounting"
date: 2007-06-16
forum: Gaming &amp; Leisure
---

### Post by DSn0wMan on 2007-06-16
I am installing SimCity 4 with wine. When it asks for the second disk I cab only eject it by issuing the command "wine eject".

When I insert disc2 it is un-readable. I think ejecting it is corrupting something. Once I restart, I can read the disk just fine.

Any Ideas on how to do a multiple disk install with wine?

---

### Post by DSn0wMan on 2007-06-16
I just got it to work by following the advice here.

[http://frankscorner.org/index.php?p=simcity4](http://frankscorner.org/index.php?p=simcity4)

and kicking it off like so ```
WINEDEBUG=-all env WINEPREFIX="/home/${USER}/.wine" nice -20 wine "C:\games\SimCity4\Apps\SimCity 4.exe" -intro:off
```

---

### Post by Cappy on 2007-06-16
It also works if you navigate Nautilus (the file browser) to your CD (or double click on the CD on your Desktop) and Double click the Setup.exe or Install.exe

Or right click the exe and select "Open with" and select "wine" (or type it if not available).

---

### Post by cogadh on 2007-06-17
However, doing it that way can sometimes actually cause the CD swap error, if Nautilis is accessing the disk when the install application requests the CD change.

---

