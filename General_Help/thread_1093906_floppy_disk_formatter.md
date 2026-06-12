---
title: "floppy disk formatter"
date: 2009-03-12
forum: General Help
---

### Post by Len Tyree on 2009-03-12
having trouble formatting floppy disks.

tried to use 'gfloppy' but was told "cannot initialize device".

tried to copy down via apt-get, received following "gfloppy package not available but is referred to by another package'; did not say which or what; stated also 'package may be missing, obsoleted, or only available from another source??

anyone have any ideas?  

thanks, len tyree.

---

### Post by plucky on 2009-03-12
> **Len Tyree said:**
> having trouble formatting floppy disks.

tried to use 'gfloppy' but was told "cannot initialize device".

tried to copy down via apt-get, received following "gfloppy package not available but is referred to by another package'; did not say which or what; stated also 'package may be missing, obsoleted, or only available from another source??

anyone have any ideas?  

thanks, len tyree.

gfloppy is part of the gnome-utils package and should be under **System Tools** in the **Applications** menu.```
sudo apt-get install gnome-utils
```

Have you installed the floppy driver? ```
sudo modprobe floppy
```


Good Luck

---

### Post by Len Tyree on 2009-03-12
thanks plucky.

already had gnome-utils but didn't know it or about it.

now all i need to do is get permission to use it.

Thanks again, len tyree.

---

### Post by plucky on 2009-03-12
> now all i need to do is get permission to use it.


Add this line to /etc/fstab if it is not already there ```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
``` and make sure there is a floppy0 directory with ```
sudo mkdir /dev/floppy0
``` and then reboot.Also add yourself to the floppy group.Type ```
id
``` in a terminal to determine if your user is in the floppy group.Use **System > Administration > Users and Groups** to add your user to the floppy group.


Good Luck

---

### Post by Len Tyree on 2009-03-24
SOLVED...   with pluckys advice am now able to format the little ones...

---

### Post by jbfriend on 2009-04-19
> **plucky said:**
> gfloppy is part of the gnome-utils package and should be under **System Tools** in the **Applications** menu.```
sudo apt-get install gnome-utils
```

Have you installed the floppy driver? ```
sudo modprobe floppy
```


Good Luck

the two lines of code did the trick for me! thank you!

jack

---

