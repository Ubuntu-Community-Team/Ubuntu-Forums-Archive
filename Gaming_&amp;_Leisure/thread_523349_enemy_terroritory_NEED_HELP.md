---
title: "enemy terroritory NEED HELP"
date: 2007-08-11
forum: Gaming &amp; Leisure
---

### Post by Icenate001 on 2007-08-11
hey ... thanks for reading even if you arent a pro could you please tell what i need to get or why its failing if i try to use.. sh ./et-linux-2.55.x86.run it still wont work it will say authorization failed



nathan@Computer:~/Desktop$ sudo ./et-linux-2.55.x86.run
Password:
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
/home/nathan/.setup22632: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

---

### Post by jeremy1138 on 2007-08-11
right click on the file - select preferences - click on the permissions tab - check the box next to allow allow executing file as a program.

Maybe this will work...  I'm not really sure.  I'm no expert either lol.

---

### Post by Nameless One on 2007-08-11
:lolflag:
Should be fixed with a simple
```
sudo apt-get libgtk1.2
```
at the console.

---

### Post by MepisReign on 2007-08-11
Also, that version is kind of old, u should install 2.60 version.
By installing the 2.55 version u may not be able to connect to virtually no servers.

Regards,

MepisReign

---

### Post by Icenate001 on 2007-08-13
thank you so much do guys by happen chance know how to update it.. lol... it just closes out on me when it needs to download stuff to play on  a server in game?

---

### Post by Crenfinkle on 2007-08-14
HA! No wonder I couldn't connect! They really need a single player mode on that game IMO

---

