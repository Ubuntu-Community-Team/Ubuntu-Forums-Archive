---
title: "how to remove a user from ubuntu?"
date: 2009-04-12
forum: General Help
---

### Post by ayastona on 2009-04-12
how can i completely delete a user account from my system?

---

### Post by connorh123 on 2009-04-12
System/Administration/Users and Groups/ then unlock it, click on the name, then click delete.

---

### Post by Peasantoid on 2009-04-12
```
userdel <username>
```

---

### Post by ayastona on 2009-04-12
i did the userdel command and it came back saying that it was unable lock the password file.. what does that mean?

---

### Post by Yashiro on 2009-04-12
It means you should use the graphical tool.

---

### Post by Iowan on 2009-04-12
```
**sudo **userdel <username>
```

---

### Post by mb_webguy on 2009-04-13
Deleting the user account won't delete the user home directory, btw. You'll have to do that manually with either "sudo rm -r /home/*username*" or with Nautilus opened with root privileges ("gksu nautilus").

---

### Post by Copernicus1234 on 2009-04-13
> **mb_webguy said:**
> Deleting the user account won't delete the user home directory, btw. You'll have to do that manually with either "sudo rm -r /home/*username*" or with Nautilus opened with root privileges ("gksu nautilus").

Or "sudo userdel -f username", that removes the home directory as well.

---

