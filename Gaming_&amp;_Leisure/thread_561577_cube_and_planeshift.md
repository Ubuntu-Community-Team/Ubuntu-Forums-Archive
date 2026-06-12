---
title: "cube and planeshift"
date: 2007-09-27
forum: Gaming &amp; Leisure
---

### Post by nofx135 on 2007-09-27
can someone pleaz tell me how to install cube, cube 2, assault cube, and planeshift on my ubuntu 7.04


or are there better fps and mmo/rpg games out for linux?

---

### Post by StJimmy on 2007-09-27
cube, cube2 and assaultcube are easy to install.

Just download the archive file, just extract them (right click>Extract here) Then open the extracted folder and double click on the "cube_unix" file for cube, the "sauerbraten_unix" file for cube2 or the "assaultcube.sh" file for assualtcube, and then click "run" when the options pop up.

If nothing happens when you click, right click the file you're trying to execute and go to properties > permissions > and check off  "Execute" if it's not.

I'm sorry, I'm not sure about planeshift, as I haven't tried it yet, but I play the others regularly.

---

### Post by nofx135 on 2007-09-27
> **StJimmy said:**
> cube, cube2 and assaultcube are easy to install.

Just download the archive file, just extract them (right click>Extract here) Then open the extracted folder and double click on the "cube_unix" file for cube, the "sauerbraten_unix" file for cube2 or the "assaultcube.sh" file for assualtcube, and then click "run" when the options pop up.

If nothing happens when you click, right click the file you're trying to execute and go to properties > permissions > and check off  "Execute" if it's not.

I'm sorry, I'm not sure about planeshift, as I haven't tried it yet, but I play the others regularly.

ive tried executing these files but nothing happens (w/ the checked off execute box in properties)
how do i install it so that i can acess these games through the application menu like any other program

---

### Post by StJimmy on 2007-09-27
Then try opening your terminal and doing 
```
cd Desktop/file/location
chmod +x cube_unix
```

Then executing it. Do the same for AssaultCube and Cube2.

---

### Post by nofx135 on 2007-09-27
> **StJimmy said:**
> Then try opening your terminal and doing 
```
cd Desktop/file/location
chmod +x cube_unix
```

Then executing it. Do the same for AssaultCube and Cube2.

~$ cd Desktop
~/Desktop$ cd AssaultCube
~/Desktop/AssaultCube$ 

thats where i am at now what

---

### Post by nofx135 on 2007-09-27
can someone just tell me how to simply install it, is there a deb or is this crap in the repositories

---

### Post by bwakkie on 2007-10-11
For Planeshift:

Download the bin file from [www.planeshift.it ]("http://www.planeshift.it")and change the installer permissions...

```
chmod +x planeshift.bin
```

...and run the installer

```
./planeshift.bin
```

then follow the instructions.

I myself have problems with the graphics at the moment. At home I have a compiled version under Gentoo which is working without any problems. And on top of that I run compiz which gives problems on all my games. So before starting to play disable compiz I would say.

---

