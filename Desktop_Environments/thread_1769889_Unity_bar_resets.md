---
title: "Unity bar resets"
date: 2011-05-28
forum: Desktop Environments
---

### Post by hulslanderam on 2011-05-28
I keep setting up my unity bar the way I want it to look using the "keep in launcher" option but the bar goes back to the original setup whenever I log out. Am I doing something wrong?

---

### Post by Krytarik on 2011-05-29
Check if the package "libdconf0" is installed:
```
dpkg -l |grep libdconf0
```If it isn't, install it:
```
sudo apt-get install libdconf0
```The solution is from this earlier post:
[http://ubuntuforums.org/showthread.php?p=10868407#post10868407](http://ubuntuforums.org/showthread.php?p=10868407#post10868407)

Greetings.

---

### Post by hulslanderam on 2011-06-01
I know this a late response but thanks. The weird thing is that I did it once and it didn't work yet I decided to rerun the command several days later and even though it didn't install anything new it worked. Odd... But once again thanks.:D

---

### Post by yanom on 2011-06-14
> **hulslanderam said:**
> I know this a late response but thanks. The weird thing is that I did it once and it didn't work yet I decided to rerun the command several days later and even though it didn't install anything new it worked. Odd... But once again thanks.:D

same thing here.

---

