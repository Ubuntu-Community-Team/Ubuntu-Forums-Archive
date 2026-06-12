---
title: "Starting UT2004"
date: 2009-08-02
forum: Gaming &amp; Leisure
---

### Post by Raiju on 2009-08-02
I Installed it using the 5 install cds and patched it using loki's megapack installer [http://www.liflg.org/?catid=6&gameid=17](http://www.liflg.org/?catid=6&gameid=17)


it ran after the install when it asks do you want to play?
but when i go to applications>other>ut2004 from the start menu ut doesnt start

---

### Post by Technophobia on 2009-08-02
try to run it from the console

cd /usr/local/games/ut2004

./ut2004

it should show an error in the console

---

### Post by Raiju on 2009-08-02
eric@Raiju-desktop:~$ cd /usr/local/games/ut2004
eric@Raiju-desktop:/usr/local/games/ut2004$  ./ut2004
./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
 
this is what i get

---

### Post by Technophobia on 2009-08-02
sudo apt-get install libstdc++5

will fix that

---

### Post by Raiju on 2009-08-02
Thank You! that worked for me.

Now i need to find out why i get no audio in-game

---

### Post by epitaph on 2009-08-02
Typically pulseaudio would manage that, but if you have removed pulseaudio and you have no hardware mixing on your sound device another application may be taking over /dev/dsp and preventing UT2004 from outputting sound.

First, try running ut2004 from a console with the aoss wrapper:

```
aoss ut2004
```

See if that gives you sound. Also, launch ut2004 from a console and see if you get any information about the sound system.

---

