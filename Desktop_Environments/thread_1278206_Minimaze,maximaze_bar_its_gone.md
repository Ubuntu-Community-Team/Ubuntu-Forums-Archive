---
title: "Minimaze,maximaze bar its gone"
date: 2009-09-29
forum: Desktop Environments
---

### Post by neotifa on 2009-09-29
Hi everyone, since this is my first post.
I have this problem with compiz (wich i thnk it is). When i activate my background effects to extra, the upper bar with mininize, maximize, unmaximaze its missing. When its not activated, the bar is here. Using ubuntu 8.10, (i had mac4lin theme few days ago, could that be the problem?)
Here is picture
[[IMG]http://img62.imageshack.us/img62/9528/screenshote.th.png[/IMG]]("http://img62.imageshack.us/i/screenshote.png/")

---

### Post by ~sHyLoCk~ on 2009-09-29
Open terminal type:
```

compiz --replace&
```

---

### Post by neotifa on 2009-09-29
```
/usr/bin/compiz.real (core) - Warn: no GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Info: Coudn't bind redirected window 0x00046 to texture 
```
still not working

---

### Post by wojox on 2009-09-29
```
metacity --replace
```

---

### Post by neotifa on 2009-09-29
The terminal is now stuck with metacity --replace !

---

### Post by wojox on 2009-09-29
oops, Alt+F2 not the terminal.

---

### Post by neotifa on 2009-09-29
Same thing, notting happes

---

### Post by wojox on 2009-09-29
You may try going over to the compiz site and looking for a solution. Depending on what you graphics card is.

---

### Post by neotifa on 2009-09-29
I'l try to reinstall compiz and my graphic card.
How to completly uninstall my graphical card and compiz?

---

### Post by lidex on 2009-09-29
Try this first - install compiz settings manager:
```
sudo apt-get install compizconfig-settings-manager
```

Once installed (if not already) go to "System>Preferences>CompizConfig Settings Manager. Under "Effects" click on the "Window Decoration" tile. In the "Command" field enter
```
metacity --replace
``` or if Emerald is installed:
```
emerald --replace
```
reboot

---

