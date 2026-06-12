---
title: "how to get vmware to comile in breezy"
date: 2005-10-14
forum: Desktop Environments
---

### Post by drews_blunted on 2005-10-14
:KS 

ok, so i just upgraded to breezy i love it!

i cannot compile vmware because it doesnt work with gcc 4.0 how can i get it to install on breezy?

anyhelp is much welcomed!

---

### Post by chaumurky on 2005-10-14
at at terminal enter:
```
export CC=gcc-3.4
``` 
then try again

EDIT: oh, make sure it's installed beforehand:

```
sudo apt-get install gcc-3.4
```

---

### Post by drews_blunted on 2005-10-15
[http://ubuntuforums.org/showthread.php?t=65638&highlight=vmware](http://ubuntuforums.org/showthread.php?t=65638&highlight=vmware)

That thread helped me alot too

The above command you gave me was all so neccesary for me to get this installed! Thank you very much! :KS

---

