---
title: "auto-mount"
date: 2009-05-01
forum: General Help
---

### Post by Bigneil on 2009-05-01
How do i go about asking my ubuntu to automatically mount the second hard drive in my pc at start up ?

---

### Post by codeseer on 2009-05-01
```

gksudo gedit /etc/fstab

```

You will need to make a directory for your mount point, naming it what you wish in the /media directory.

You can get the UUID by running this:

```

sudo blkid

```

---

### Post by taurus on 2009-05-01
What filesystem is that second harddrive?  You just need to add an entry in /etc/fstab to have it mount automatically each time you boot Ubuntu.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Bigneil on 2009-05-01
Hi, thanks for your replies. its an ntfs partition, i currently use it for storing media and some back up files.  


I did the 'sudo blkid'  and got the uuid. 

i'm not sure i understand how fstab works?

here is a screen shot of the terminal.

---

### Post by taurus on 2009-05-01
Install ntfs-config and use it to configure your ntfs drive then.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by codeseer on 2009-05-01
> **Bigneil said:**
> Hi, thanks for your replies. its an ntfs partition, i currently use it for storing media and some back up files.  


I did the 'sudo blkid'  and got the uuid. 

i'm not sure i understand how fstab works?

here is a screen shot of the terminal.

```

UUID=WhateverItIs    /media/something    ntfs    users,defaults,umask=000    0    0

```

Use the TAB key to separate columns.

---

### Post by Bigneil on 2009-05-02
thanks very much. i got it sorted, thanks to your help guys.:P

---

