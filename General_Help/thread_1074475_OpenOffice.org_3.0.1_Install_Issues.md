---
title: "OpenOffice.org 3.0.1 Install Issues"
date: 2009-02-19
forum: General Help
---

### Post by Bullhead on 2009-02-19
Ok, I know there his a how-to in the archives. I read it and followed the instructions, but I keep on getting this error message: 
```

chris@chris-laptop:~$ sudo dpkg -i ~/Desktop/000300_m15_native_packed-1_en-US.9379/DEBS/*.deb

dpkg: error processing /home/chris/Desktop/000300_m15_native_packed-1_en-US.9379/DEBS/*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/chris/Desktop/000300_m15_native_packed-1_en-US.9379/DEBS/*.deb

```
Wondering if anyone could tell me what i'm doing wrong?

---

### Post by taurus on 2009-02-19
Are you sure you have the name of the directory right?  Instead of using the long path, why not just cd, change directory, to it first before you try to install it.  

```
cd ~/Desktop
cd 000300_m15_native_packed-1_en-US.9379
ls -la
```

---

### Post by Bullhead on 2009-02-22
Thank you very much for the help. After reading your post, I saw that the file I had did not contain the /DEBS folder because I had downloaded the RPM install.

---

