---
title: "Script to change screen resolution"
date: 2009-01-28
forum: Desktop Environments
---

### Post by blazemore on 2009-01-28
We all know the problems with World of Goo:

* It breaks if you have Compiz on
* It doesn't change the screen resolution back afterwards

Is there a way I can make a script to change to metacity (metacity --replace), run world of goo (wine .wine/drive_c...) and then **change the resolution back after the program quits**?

---

### Post by blazemore on 2009-01-29
*bump* tiem

---

### Post by XanTrax on 2009-01-29
Here you go :)

[http://ckozler.net/?p=27](http://ckozler.net/?p=27)

You can run it as:

```
startgame -wine "/home/yourname/.wine/drive_c/Program Files/World Of goo/worldofgoo.exe"
```

The above is an example of what you will probably run.  You can give my script a try and see what happens.

Copy all the text in the area and then save it.  Chmod 755 and give it a whirl.

My script does not change the resolution back to what it was but I can modify it as such.

---

### Post by XanTrax on 2009-01-29
Double post, I know...

I just looked over the script and I realized that wordpress, for whatever reason, randomly decided to put an an amp; after the & in the code.  Please copy the script again, I have removed it and fixed it.

---

### Post by blazemore on 2009-01-29
Cheers for that, it looks like it could be useful.
However, I get errors:
```
rory@rory-desktop:~$ game -wine "/home/rory/.wine/drive_c/Program\ Files/WorldOfGoo/WorldOfGoo.exe"
Metacity found.
Compiz found.
*** NOTIFICATION: Compiz found. Replacing with metacity. ***
*** NOTIFICATION: Killing all instances of Compiz. ***
*** NOTIFCATION: Killed compiz successfully. ***
*** NOTIFCATION: Replacing with metacity. ***
*** NOTIFCATION: Metacity ran successfully. ***
Wine found
wine: cannot find '/home/rory/.wine/drive_c/Program\'

```

Yes I saved it as /usr/bin/game

---

### Post by blazemore on 2009-01-29
No worries I sorted it.

Any ideas about the screen resolution; that's the main problem.

---

### Post by XanTrax on 2009-01-29
> **blazemore said:**
> No worries I sorted it.

Any ideas about the screen resolution; that's the main problem.

For you though, because you brought it to my attention, I can get the screen resolution, save it, and compare it to the current set resolution.  If its not equal to the current, it will reset to the previously set one.  I will keep you updated ;).

---

### Post by blazemore on 2009-01-30
So you know the commands for changing resolution? Are there any apps I should have installed? Anything to change in xorg.conf?

---

### Post by XanTrax on 2009-01-30
> **blazemore said:**
> So you know the commands for changing resolution? Are there any apps I should have installed? Anything to change in xorg.conf?

xrandr and another command but the binaries are already in Ubuntu.  I will let you know when I update it.

---

