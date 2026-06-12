---
title: "bin file problem"
date: 2009-05-25
forum: General Help
---

### Post by m_adel on 2009-05-25
hi..

after downloading jdk-6u13-linux-i586.bin from sun.com 
i changed the jdk-6u13-linux-i586 mode to +x 
but still cant execute it:
from terminal this massege appears:
-bash: jdk-6u13-linux-i586.bin: command not found

when i double click the file :
There is no application installed for this file type

---

### Post by taurus on 2009-05-25
Were you in the right directory when you tried to run it?  Also, don't forget to include the ./ in front of the filename since that directory is not in your path.

```
sudo ./jdk-6u13-linux-i586.bin
```

---

### Post by m_adel on 2009-05-25
thnx it works
but what is the meaning of ./

---

### Post by albinootje on 2009-05-25
> **m_adel said:**
> thnx i works
but what is the meaning of ./

. equals the current directory. 
By default the current directory is not in the PATH, I think for security reasons.

---

### Post by _Purple_ on 2009-05-25
The dot represents the current directory. You need to place ./ before the file name to execute it if they are not in your path. You can see the list of path using ```
$PATH
```

---

