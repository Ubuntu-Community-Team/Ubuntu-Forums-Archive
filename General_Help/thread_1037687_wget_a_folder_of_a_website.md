---
title: "wget a folder of a website?"
date: 2009-01-12
forum: General Help
---

### Post by frenchn00b on 2009-01-12
Hello,

I would like to make a backup of my website with html, wget:
```
 wget -r -l4 -t2 -N "http://.... $x/" 
```
I used l of 4 and recursive, and $x is the concerned folder.


Is that the way? cuz it downloads also everywhere :) :( :( :(  the other html ?

---

### Post by hikaricore on 2009-01-12
You should try httrack.

```
sudo apt-get install httrack
```

You'll want to then either read the man pages:

```
man httrack
```

Or lookup basic use on the httrack website.

---

