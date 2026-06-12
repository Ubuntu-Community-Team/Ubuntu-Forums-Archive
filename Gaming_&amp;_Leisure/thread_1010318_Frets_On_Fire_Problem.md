---
title: "Frets On Fire Problem"
date: 2008-12-13
forum: Gaming &amp; Leisure
---

### Post by |{urse on 2008-12-13
I just installed FoF from the gutsy repos. This game looks nice all the in menu sounds work and the preview of the songs work but when i try to play (with the f1 f2 f3 f4 f5 keys) the sound disappears completely. Like the songs stop playing. My google skills have failed me, anyone know how to fix this?

---

### Post by |{urse on 2008-12-17
WHYYYYYYYYYYYYYYYYYYYYYYYYYYYY!

bump

---

### Post by sbennettgso on 2008-12-20
DON'T install this game from the repositories.  Download it from the Frets on Fire WWW site and extract it to the desktop or a temp folder somewhere.  This game uses the Python interpreter, so you can overwrite the existing files.  

The version from the repositories installs in /usr/share/games/fretsonfire/.  Once you give yourself the appropriate write permissions for this directory and its subdirectories using the chmod command (which I did so I can add songs; alternatively you can perform these operations as sudo), you should be able to copy the files from the extracted folder to the folder listed above.

One thing you will have to do is change the execution script.  It should be located in /usr/games/.  As sudo, edit the file "fretsonfire" replacing the lines as follows:

Is:
```
cd /usr/share/games/fretsonfire/game/
./FretsOnFire.py "$@"
```

Needs to be:
```
cd /usr/share/games/fretsonfire/src/
./FretsOnFire.py "$@"
```

One other thing I've noted on this game.  If you use song files from the internet, you have to make all the file names all lower case.

Hope this helps.  I had the same problem when I installed this about a week ago, and this morning using the version from the Frets on Fire site it seems to work now.

Thanks,
Scott

---

### Post by |{urse on 2009-02-03
sorry for the late late reply but this worked awesome ^^

thanks!

/me clicks imaginary thanks button

---

