---
title: "How do I install dekorator?"
date: 2009-09-01
forum: Desktop Environments
---

### Post by Aaron_Griffiths_92 on 2009-09-01
I just installed KDE over my Gnome Ubuntu, and i want to know how to get dekorator please.

---

### Post by Aaron_Griffiths_92 on 2009-09-01
anyone? sudo apt-get isnt working

---

### Post by krazyd on 2009-09-01
dekorator is for kde 3, while kubuntu since 8.10 has been kde 4.
You can get themes here: [http://www.kde-look.org/index.php?xcontentmode=9](http://www.kde-look.org/index.php?xcontentmode=9)
and window decorations here: [http://www.kde-look.org/index.php?xcontentmode=76](http://www.kde-look.org/index.php?xcontentmode=76)

Edit:
Actually, there is a port of dekorator to kde4 :)
[http://www.kde-look.org/content/show.php/deKorator?content=87921](http://www.kde-look.org/content/show.php/deKorator?content=87921)

You can compile it yourself following the instructions on that page, though it looks as though someone in the comments has made a .deb for kubuntu 9.04.

---

### Post by barnex on 2009-09-01
I installed dekorator in kde4:

```
sudo apt-get install kwin-style-dekorator
```

It should allow kde3 window decorations to be used in kde4. You need to import the themes in systemsettings, under appearance>windows>dekorator.
I couldn't get it to work though, as it crashed. But it should be possible...

---

