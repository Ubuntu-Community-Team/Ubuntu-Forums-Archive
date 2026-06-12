---
title: "&quot;Not owned by you&quot; on Ubuntu 9.04"
date: 2009-05-12
forum: General Help
---

### Post by Raptor Jesus on 2009-05-12
I get this error when I try to run an .exe with Wine. 

Here is the error message: 
> 
wine: /home/robert/.wine is not owned by you

I tried to run the .exe with Wine as root.. but it doesn't work.

Any help will be appreciated.

---

### Post by anjilslaire on 2009-05-12
1st, you shouldn't need to run wine as root.
2nd, you can ensure your .wine directory (and your entire home folder) is owned by you as follows:
```
sudo chown -R robert:robert /home/robert
```

---

### Post by bodhi.zazen on 2009-05-12
From the wine FAQ :

[http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014](http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014)

---

### Post by Raptor Jesus on 2009-05-12
chown: cannot access `/home/robert/.gvfs': Permission denied

... Dunno what happened :(

---

### Post by Tipped OuT on 2009-05-12
Try it again, using the File Browser as root. To do this type **sudo nautilus** in terminal.

---

