---
title: "UT2004 Demo won't start"
date: 2007-07-21
forum: Gaming &amp; Leisure
---

### Post by pofigster on 2007-07-21
Ok, so, I downloaded the UT2004 demo (my roommate was practically frothing at the mouth waiting for it).  I installed it via:

$ sudo sh UT2004...3334.run

This brought up the GUI like it was supposed to and the game installed fine.  When it was done installing it asked if I would like to start.  I said yes, for a split second I saw the UT2004 splash screen and the game started.  I played a quick game and quit.

Next I tried to relaunch the program from the Applications menu - I again saw the splash screen for a split second and then ... nothing.  No hang up, no crash, nothing.  It was like I hadn't done anything at all.

I'm curious why that would be - any help on how to get the game to launch again?  Do I need to log in as root and chmod the folder that contains it to read/write?  [-o<

Thanks!

---

### Post by rajeev1204 on 2007-07-21
Run it from the terminal and see what errors it gives .

Will help u better diagnose the problem

---

### Post by Cappy on 2007-07-21
Actually .. yes .. yes you do need to chmod your .ut2004 ^^ Bug in the installer if you hit "play" right after it installs.
```
sudo chown -R $USER:$USER ~/.ut2004
```
```
sudo chmod -R 770 ~/.ut2004
```

Btw when a program doesn't launch run it on the command line to get the error output. For instance: ```
ut2004
``` in this case.

---

### Post by ShangTsungOmega on 2007-08-07
here's my error message :

jerry@jerry-desktop:~$ ut2004
Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History: 

Exiting due to error

---

### Post by Cappy on 2007-08-07
try what I said above =-/

---

