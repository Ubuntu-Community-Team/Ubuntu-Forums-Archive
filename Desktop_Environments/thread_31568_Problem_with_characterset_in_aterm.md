---
title: "Problem with characterset in aterm"
date: 2005-05-03
forum: Desktop Environments
---

### Post by OldPlanet on 2005-05-03
My locale is set to UTF-8, and i want to keep it that way. But i am wondering, is it possible to force aterm to use ISO 8859-15? Aterm doesn't even support UTF-8 (when i type special-characters like æøå, they are displayed wrong). I want to use aterm for IRC (irssi), and i prefer to use ISO 8859-15.

---

### Post by liljencrantz on 2005-05-03
Have you tried simply setting the LANG variable to en_US.iso885915 in aterm?

---

### Post by OldPlanet on 2005-05-04
Yes, that works. But won't that affect the entire system?

---

### Post by liljencrantz on 2005-05-04
[QUOTE=OldPlanet]Yes, that works. But won't that affect the entire system?[/QUOTE]
 Depends. If you set an environment variable in one process, it will only affect that process and all it's children, which is exactly the behaviour you want. But if you set the variable in a common configuration file, this change may be other processes as well.

One way to set this variable on only that term would be to use something like

aterm -e "export LANG=en_US.iso885915;bash"

for starting aterm. This of cours assumes you run bash.

---

### Post by OldPlanet on 2005-05-04
Thankyou, you are right  :)

I am now using this simple script to run irssi:
```
#!/bin/sh
export LANG="en_US.ISO-8859-15"
aterm -e irssi
```

---

