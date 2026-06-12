---
title: "Making KDE look like OsX"
date: 2006-08-02
forum: Desktop Environments
---

### Post by benjfield on 2006-08-02
Hi, In the last distro of ubuntu, it was possible to make KDE basically look like Os X (which im quite a fan of). I was wondering if anyone could link a site, or tell me themselves how I'd go about doing it again in dapper. Cheers.

---

### Post by Ramses de Norre on 2006-08-02
The same way as in breezy?? It's all about themes, icon sets, wallpapers, gdesklets and things like that.
All of them work the same in both versions of ubuntu.

---

### Post by aysiu on 2006-08-02
Enable the Universe repository.
```
wget -c http://www.alltimetv.com/www.WinMatrix.com/Apple_OSX_Wallpapers/Gallery_1/Aqua%20Blue.jpg
sudo aptitude update
sudo aptitude install kwin-baghira kpersonalizer
kpersonalizer
``` Select Mac OS and Baghira. Then select the wallpaper you downloaded.

---

### Post by aysiu on 2006-08-02
Enable the Universe repository.
```
wget -c http://www.alltimetv.com/www.WinMatrix.com/Apple_OSX_Wallpapers/Gallery_1/Aqua%20Blue.jpg
sudo aptitude update
sudo aptitude install kwin-baghira kpersonalizer
kpersonalizer
``` Select Mac OS and Baghira. Then select the wallpaper you downloaded.

---

### Post by ajgreeny on 2006-08-02
Have a look at *kxdocker* and *superkaramba* as well.

---

### Post by benjfield on 2006-08-02
Ok I tried what you said but i was told...

Couldn't find any package whose name or description matched "kwin-baghira"

Any Suggestions?

Thanks

---

### Post by aysiu on 2006-08-02
> **benjfield said:**
> Ok I tried what you said but i was told...

Couldn't find any package whose name or description matched "kwin-baghira"

Any Suggestions?

Thanks
Did you [enable extra repositories](http://www.psychocats.net/ubuntu/sources)? *kwin-baghira* is in the Universe repositories.

---

### Post by benjfield on 2006-08-02
Ok i got the package then got this far (view attachment)

What now?
Sorry for being such as n00b..

Cheers

---

### Post by aysiu on 2006-08-02
Hm. Maybe Baghira doesn't show up in KPersonalizer. That's okay. After you're done with KPersonalizer (which is a quick way to make some of the other behavior Mac-like), do ```
kcontrol
``` and change the window decorations and style to Baghira.

---

### Post by GoldBuggie on 2006-08-19
[http://baghira.sourceforge.net/OS_Clone-en.php](http://baghira.sourceforge.net/OS_Clone-en.php)

---

