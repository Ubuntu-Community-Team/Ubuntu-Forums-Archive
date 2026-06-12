---
title: "Wxsand flling sand game please HELP?!!"
date: 2006-12-24
forum: Gaming &amp; Leisure
---

### Post by MkfIbK7a on 2006-12-24
Cannot run wxsand There is a bin file on the website.[http://www.piettes.com/fallingsandgame/index.html](http://www.piettes.com/fallingsandgame/index.html)
It is possible to run the exe in wine.

---

### Post by taurus on 2006-12-24
Move to Gaming & Leisure...

---

### Post by pay on 2006-12-25
What exactly is the problem? I understand that it isn't running but is it a video issue or don't you quite get how to install it?.. We sorta need more information.
Assuming that it is in your home folder, you might need to run```
chmod 755 fsg-4.4
./fsg-4.4
```to make it executable.

---

### Post by MkfIbK7a on 2006-12-26
i cant install it heres what you said and i did

jon@albert:~$ chmod 755 fsg-4.4
jon@albert:~$ ./fsg-4.4
./fsg-4.4: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory

---

### Post by smartbei on 2006-12-26
Try this:
```
sudo apt-get install libpng3
```
That solved the issue for me.

---

### Post by MkfIbK7a on 2006-12-26
thank you so much worked perfectly!!:D

---

### Post by Kingfield on 2007-07-17
Sorry to gravedig... but i get this error when trying to run :

Segmentation fault (core dumped)

---

### Post by Eion on 2007-12-08
This dosn't work for me, i've tried every method I could find and I can't get anything to work, i've been trying all day and i'm ready to give up.  Anybody have any ideas?

---

