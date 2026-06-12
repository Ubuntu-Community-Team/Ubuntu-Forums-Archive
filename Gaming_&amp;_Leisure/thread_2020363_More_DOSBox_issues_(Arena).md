---
title: "More DOSBox issues (Arena)"
date: 2012-07-08
forum: Gaming &amp; Leisure
---

### Post by SerFaren on 2012-07-08
So, this is what I have so far (Trying to run Arena)

I extracted the Arena106.exe to the /home/NAME/dos/

it created a folder called "ARENA"

So, then I got here

```
C:\>ARENA>a.exe
```, yet for some reason it doesn't pull up Arena.

All the .exe files are as follows:
mouse.exe
A.EXE
INSTALL.EXE
ULTRAMID.EXE

Now, it's not giving me an error when I type in A or A.EXE or a.exe, INSTALL, INSTALL.EXE, etc., it's just going to the other line. Help?

****EDIT** After reading the HELP more carefully, it says that I must type INSTALL and that will bring me to a configuration screen... it doesn't.

---

### Post by Toz on 2012-07-08
Where did you get Arena106.exe from and how did you extract the file? I just went to [http://www.elderscrolls.com/arena/]("http://www.elderscrolls.com/arena/") and downloaded the game from there. I had to use wine to run Arena106.exe to uncompress the contents properly. Then running A.exe from within DosBox started up the game.

From within DosBox, what does the following return:
```
dir A.exe
```
...the size of the file should be greater than 0.

---

### Post by Perfect Storm on 2012-07-08
Please keep your issue to the thread you already started.


Thread closed.

---

