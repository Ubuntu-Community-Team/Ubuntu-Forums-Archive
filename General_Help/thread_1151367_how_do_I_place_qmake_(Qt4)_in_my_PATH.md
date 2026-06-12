---
title: "how do I place qmake (Qt4) in my PATH"
date: 2009-05-06
forum: General Help
---

### Post by ozguitarplayer on 2009-05-06
every now and and then I find that something isn't in my PATH...can someone explain how to place something in my path...

...In this case I'm trying to install the latest MuseScore program however I get this from terminal..... 

The installed Qt version 4.3.4 is too old, at least version 4.4.0 is required
CMake Error: Fatal error: QT (version >= 4.4.0) required. Cmake tries to detect QT4 by searching for 'qmake' in your PATH.If you have QT4 installed, make sure qmake is found in your PATH. If you compiled QT4 yourself make sure your new qmake ist found _first_ in your PATH.

...so I installed that according to the install instructions that came with Qt, which included adding this line to .profile:
PATH=/usr/local/Trolltech/Qt-4.5.1/bin:$PATH
export PATH
 
however when I try to install MuseScore again I am told the same message from terminal....any help appreciated.....

---

### Post by joseielpi on 2011-02-14
i'm having the exact same problem. Any news?

---

### Post by asmoore82 on 2011-02-14
```
sudo apt-get install musescore
```

---

