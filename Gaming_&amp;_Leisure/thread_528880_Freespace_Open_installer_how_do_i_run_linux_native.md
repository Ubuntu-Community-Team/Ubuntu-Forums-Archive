---
title: "Freespace Open installer how do i run linux natively?l"
date: 2007-08-18
forum: Gaming &amp; Leisure
---

### Post by cor2y on 2007-08-18
Hello i am just wondering does anyone know how to install Freespace 2 to run natively in Linux?
I came across the java based installer but it only carries windows exe or mac OS executable and the data files.

---

### Post by hikaricore on 2007-08-18
[http://ubuntuforums.org/showpost.php?p=2831809&postcount=3](http://ubuntuforums.org/showpost.php?p=2831809&postcount=3)

---

### Post by hikaricore on 2007-08-18
P.S.  If you like freespace 2, you may want to check out the Battlestar Galactica :: Beyond The Red Line (Demo) here: [http://www.game-warden.com/bsg/](http://www.game-warden.com/bsg/)

It's based on the fs2 engine and coming along nicely.  ^_^

---

### Post by cor2y on 2007-08-18
I'm afraid you will have to treat me like a raw noob.
I can't figure out how to install or play the game.

Ok got and used  the open  freespace 2 installer that had the super mega downloads depending on the files you desired to download.
It did that so now what happens?
I see only exe files do i have to run via wine or something?

---

### Post by GFree678 on 2007-08-18
[http://www.hard-light.net/wiki/index.php/Fs2_open_on_Linux](http://www.hard-light.net/wiki/index.php/Fs2_open_on_Linux)

---

### Post by cor2y on 2007-08-19
Ok figured out in order to run freespace i needed to have the mvp files in the folder.
Now i am getting this error when trying to create a new call sign in the game.
> 
Failed to save Pilot File You may be out of Disk Space.

Clicking ignore crashes to the deskto pand gives this error in the terminal
> 
ERROR: "Couldn't load pilot file, bailing" at menuui/playermenu.cpp:857



Do i have to create a folder to save pilot data?

---

### Post by cor2y on 2007-08-19
ok found the problem.
Needed to run sudo fs2_open to be able to save a pilot file.
Is this correct or do i need to chmod  something?
fs2_open is installed locally in my home folder instead of via sudo which would have put it in /usr/local/games.

---

