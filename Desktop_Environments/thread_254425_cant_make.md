---
title: "cant make"
date: 2006-09-09
forum: Desktop Environments
---

### Post by Andrew12106 on 2006-09-09
i downloaded a tar file and i extracted it and i ./configure it, but when i type "make" it wont build it. bash says it cant find the command make.

---

### Post by llamakc on 2006-09-09
Maybe you should install make.

---

### Post by mssever on 2006-09-09
You need to install build-essential before you can compile. Also, consider installing checkinstall and doing:
```
./configure && make && sudo checkinstall
```

---

### Post by keebler411 on 2006-09-09
Install the package build-essential and away you go.  For more information that might be helpfull see this article:
 [http://www.ubuntuforums.org/showthread.php?t=126199]("http://www.ubuntuforums.org/showthread.php?t=126199")

Keeb

---

### Post by aysiu on 2006-09-10
To install build essential, paste this command into the terminal: ```
sudo aptitude update && sudo aptitude install build-essential
```

---

