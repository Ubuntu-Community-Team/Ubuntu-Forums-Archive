---
title: "Compiling irssi"
date: 2006-08-04
forum: Desktop Environments
---

### Post by srunni on 2006-08-04
I was trying to compile irssi (not available in Synaptic) with gcc 4.0.3, but when I used the ```
./configure
``` command, I got the error 
```
configure: error: C compiler cannot create executables
```
According to the config.log file that it asked me to look at, the failed program was "confdefs.h". First of all, where is confdefs.h located, and secondly, will changing its permissions solve the problem? Note: this happens with ```
sudo ./configure
``` as well.

---

### Post by roostishaw on 2006-08-05
Try:
```
sudo apt-get install irssi
```

---

### Post by srunni on 2006-08-06
Wow. Can't believe I didn't try that :D
I didn't see it in Synaptic, so I didn't think it would be in "sudo apt-get install". Either way, I did the good old way, with the tarball from the site (had to go through and manually install the dep packages :D), but everything seems to be working.

---

