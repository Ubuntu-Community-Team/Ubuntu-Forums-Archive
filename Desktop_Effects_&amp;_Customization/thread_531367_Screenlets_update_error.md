---
title: "Screenlets update error?"
date: 2007-08-21
forum: Desktop Effects &amp; Customization
---

### Post by Hybrid86 on 2007-08-21
When I try to update screenlets via the update manager, I get this error message:
```
E: /var/cache/apt/archives/screenlets_0.0.10-3_i386.deb: trying to overwrite `/usr/share/applications/FlowerScreenlet.desktop', which is also in package screenlets-core

```

---

### Post by FuturePilot on 2007-08-21
I got that too. Screenlets are now all in one package instead of many like screenlets-core screenlets-extra etc. So you need to get rid of all the other screenlets packages.
```
sudo apt-get remove --purge screenlets screenlets-core screenlets-extra
```
Then reinstall screenlets
```
sudo apt-get install screenlets
```

---

### Post by Hybrid86 on 2007-08-21
Followed your instructions, and it worked, but the weather screenlet seems to be gone now :/
How do I get that back?

---

### Post by FuturePilot on 2007-08-21
It looks as though it's been left out. I've been missing that one since I updated to 0.9. I miss that one the most too.:(

---

### Post by Sunflower1970 on 2007-08-21
Oo! I know this one :)

Go here: [http://forum.compiz-fusion.org/showthread.php?t=3460](http://forum.compiz-fusion.org/showthread.php?t=3460) There are a whole bunch of updated screenlets that work with the newest version. Took me pulling out chunks of my hair (I"m bald on the sides now) but I got everything to work okay. The file is a RAR file. Once it's unpacked all the screenlets are in Tars. They'll need to be untared and put in to /usr/local/share/screenlets. Then when the screenlets-manager is run, it should pick them up.  

The weather screenlet is there. In fact there are two of them. both work fine after a test run of using them...

---

### Post by FuturePilot on 2007-08-21
You rock! Thanks! Got my weather along with a ton of new ones!:guitar:

---

### Post by Hybrid86 on 2007-08-21
Nice! Thanks you so much.

---

### Post by PaulFXH on 2007-08-22
Would appreciate some help getting the .rar file to open.
The file I downloaded is called Old Screenlets updated.rar (note the SPACES).
Then when I run
```
unrar e Old Screenlets updated.rar
```
I get
> UNRAR 3.70 beta 3 freeware      Copyright (c) 1993-2007 Alexander Roshal

Cannot open Old.rar
No such file or directory
No files to extract

which basically means it doesn't like the spaces in the name.
I also tried to rename the .rar file to something without spaces but this attempt wasn't accepted.

How did you guys do this?

---

### Post by djxcon on 2007-08-22
> Would appreciate some help getting the .rar file to open.

Try to right click on the file and click Extract Here.  This should work as long as you have unrar installed on your system.

Alternatively, you can try the following:
```
unrar e "Old Screenlets updated.rar"
```

---

### Post by PaulFXH on 2007-08-22
So, now I know. Thank you.

---

### Post by njknight on 2007-08-22
There's also a page on [http://forum.compiz-fusion.org/archive/index.php/t-3191.html](http://forum.compiz-fusion.org/archive/index.php/t-3191.html) that you might like to read ref starting the screenlets, if the manager is not installed

---

