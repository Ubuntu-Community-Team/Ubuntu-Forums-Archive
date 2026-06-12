---
title: "cedega + point 2 play"
date: 2005-03-13
forum: Desktop Environments
---

### Post by NateC on 2005-03-13
I have the files :


point2play-1.3.3-1.i386.deb
transgaming-fontinstaller_1.0_i386.deb
transgaming-mozctlinstaller_1.0-1_i386.deb


How do I install them? 


> sudo dpkg -i point2play-1.3.3-1.i386.deb  does not work. 

I get the error: 

> dpkg: error processing point2play-1.3.3-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 point2play-1.3.3-1.i386.deb


---

### Post by DJ_Max on 2005-03-13
Thats the correct way to install them, but you have to be in the right directory.
```
ls
```
Will give you the list of files in your current directory.

---

