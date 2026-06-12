---
title: "dpkg qustion"
date: 2009-03-03
forum: General Help
---

### Post by Liraz_e on 2009-03-03
well i'm working on a 8.04 desktop ubuntu when i'm trying to create an iphone cydia repository with dpkg.

i'm working with this guide : [http://www.modmyi.com/forums/cydia-support/402221-how-make-cydia-repository.html](http://www.modmyi.com/forums/cydia-support/402221-how-make-cydia-repository.html)

and when i get to step 17 i need to use the command : 

```
dpkg-scanpackages -m . /dev/null -->Packages
```

to create a packages file for the repository.

the thing is when i'm using the command i get an error :

```
Binary dir /dev/null not found
```

can any 1 help me with it pls ?

ty very much :D

---

### Post by ibuclaw on 2009-03-03
```
sudo apt-get install dpkg-dev
```
and try it again ;)

Regards
Iain

---

### Post by Tek-E on 2009-03-03
Now. Im not 100% sure on this but it could be because you are not working inside a Mac environment.  Mac OS X runs a unix derivative called darwin that runs a little bit different from the way Ubuntu's Terminal does.

---

### Post by Liraz_e on 2009-03-03
> **tinivole said:**
> ```
sudo apt-get install dpkg-dev
```
and try it again ;)

Regards
Iain

well i allready have it m8 ....

> **Tek-E said:**
> Now. Im not 100% sure on this but it could be because you are not working inside a Mac environment.  Mac OS X runs a unix derivative called darwin that runs a little bit different from the way Ubuntu's Terminal does.

mm any idea then what can i do ?

---

### Post by ibuclaw on 2009-03-03
Yes, make sure you put a fullstop between -m and /dev/null.

Spot the difference:
[PHP]$ dpkg-scanpackages -m . /dev/null -->Packages
 Wrote 0 entries to output Packages file.
[/PHP]
[PHP]$ dpkg-scanpackages -m /dev/null -->Packages
dpkg-scanpackages: error: Binary dir /dev/null not found
[/PHP]

To paste into a terminal, press **Ctrl+Shift+V**

Regards
Iain

---

