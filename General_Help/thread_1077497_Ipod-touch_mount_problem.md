---
title: "Ipod-touch mount problem"
date: 2009-02-22
forum: General Help
---

### Post by epqr on 2009-02-22
im using this [guide]("http://209.85.129.132/search?q=cache:183yOQFFVy4J:https://help.ubuntu.com/community/PortableDevices/iPhone+site:help.ubuntu.com&ct=clnk&cd=1")(Link is from google cache, since the ordinary page is down.)

so when i put in the command "ipod-touch-mount" i get;

 ```
user@user-laptop:~$ ipod-touch-mount
touch: cannot touch `/media/ipod/test': Permission denied
Unable to write to /media/ipod.  Please adjust permissions and try again.
```

What can i do?

---

### Post by Cheesemill on 2009-02-22
Try doing
```
sudo ipod-touch-mount
```

Cheesemill

---

### Post by epqr on 2009-02-22
You are noty realy supose to run that command as root (or so i have been told)

```
user@user-laptop:~$ sudo ipod-touch-mount
[sudo] password for jonesu2: 
Please add yourself to the fuse group, logout/in and try again.

```

---

### Post by epqr on 2009-02-22
Yeah so i added myself and root to the fuse group, and ran "sudo ipod-touch-mount", and it worked. Thanks!

---

