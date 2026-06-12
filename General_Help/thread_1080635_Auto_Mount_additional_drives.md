---
title: "Auto Mount additional drives"
date: 2009-02-25
forum: General Help
---

### Post by MickSulley on 2009-02-25
Hi,
I have a desktop with 3 hard drives.  How can I auto mount one or both of the other drives when I log in.  I have created a mount point called DataStore and a script as follows

mount /dev/sdc1 /media/DataStore -t ntfs -o unmask=0002,nls=utf8

and added this to run at startup but it does not seem to do anything.

I'm sure this is a fairly easy thing to do but cannot figure it out, can anyone help me please?

Thanks

Mick

---

### Post by pdwerryhouse on 2009-02-25
At login time, or at boot up?

If you want it done at boot up, then put a line like this in your /etc/fstab file:

```
/dev/sdc1 /media/DataStore ntfs umask=0002,nls=utf8     0       0
```

Note that in your line, you've put "unmask", not "umask", which is possibly why it is failing for you.

If you want to mount it at login time, I suggest a better way to do it would be to look at autofs, which is an automounter.

Cheers.

---

### Post by smani on 2009-02-25
The common way of doing this is adding an entry to the fstab (/etc/fstab). An example line:
/dev/sda1 /media/win_c ntfs-3g defaults,locale=en_US.UTF-8 0 0

Doing it by script requires root permissions, i.e. you would need a script like
```

#!/bin/bash
gksudo mount /dev/sdc1 /media/DataStore -t ntfs -o umask=0002,nls=utf8

```
which though would be annoying as you have to enter you password at each login.

Edit: got anticipated:d

---

### Post by MickSulley on 2009-02-25
Perfect!  DataStore is now mounted when I log in.

Thanks to you both

Mick

---

