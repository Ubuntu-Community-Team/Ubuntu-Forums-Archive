---
title: "How to install diablo 2 / Wine 0.9.11"
date: 2006-04-11
forum: Gaming &amp; Leisure
---

### Post by finch on 2006-04-11
Can anyone help me to install Diablo 2 on Ubuntu 5.10 / Wine 0.9.11 ?
Here what i try :
```

root@finch:~# wine /media/cdrom0/install.exe
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
root@finch:~#

```
Where the problem could be?

---

### Post by slipk487 on 2006-04-11
open the cd drive and right click the autorun.exe and select run whth wine and wine isnt to great about detecting the cd drive well so when use the D2Loader here insted of the regluar program starter

[D2Loader 1.11b]("http://http://www.d2sector.net/downloads/index.php?act=view&id=242")

---

### Post by DoktorSeven on 2006-04-11
And don't use Wine as root.

---

### Post by finch on 2006-04-12
Here what`s happen :
[http://img80.imageshack.us/my.php?image=screenshot7mn.png]("http://img80.imageshack.us/my.php?image=screenshot7mn.png")

Do you know why?

---

### Post by minisori on 2006-04-12
Run winecfg and look in drives if the type for /media/cdrom0 is CD-ROM.

---

