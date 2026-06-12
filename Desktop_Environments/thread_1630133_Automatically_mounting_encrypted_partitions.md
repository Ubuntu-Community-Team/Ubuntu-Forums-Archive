---
title: "Automatically mounting encrypted partitions"
date: 2010-11-24
forum: Desktop Environments
---

### Post by ankle on 2010-11-24
I've created some encrypted partitions using Disk Utility, and would like them to be automatically mounted when Ubuntu starts up. Is there a guide to this anywhere?

I've gathered that it involves /etc/crypttab and possibly /etc/init.d/cryptdisks, but haven't had much success so far.

Ideally, some of the partitions would mount early in the boot process, while some of them can mount after I've logged in.

---

### Post by dargaud on 2010-11-28
If it mounts automatically, what point is there in encrypting it ? Seriously.

---

### Post by ankle on 2011-06-05
Dargaud, I think you're reading that they should mount completely automatically - I mean that they should mount automatically *after I've entered the passphrase*.

---

### Post by 3Miro on 2011-06-05
In your /etc/crypttab you should have line of the form:

```
sdaX_crypt <the UUID number of the partition> none luks
```

Then in fstab, you should have:

```
/dev/mapper/sdaX_crypt /media/folder_name ext4 defaults 0 0
```

sdaX should be the partition that you encrypted

UUID can be found with the command
```
 ls -al /dev/disk/by-uuid
```

Arch Linux has a great Tutorial that helped me a lot:

[https://wiki.archlinux.org/index.php/System_Encryption_with_LUKS](https://wiki.archlinux.org/index.php/System_Encryption_with_LUKS)

---

### Post by quadra on 2011-07-30
Hi there, on my Ubuntu 11.04, when I edit /etc/crypttab as suggested, I cannot enter the passphrase during startup. The prompt is only displayed for a fraction of a second...

---

### Post by 3Miro on 2011-08-01
Sorry for the delay. Does it help if you change the last part of the fstab to:
```
... default 0 2
```
or
```
... default 0 1
```

I think "0 1" should be only used for /, the other partitions should be "0 0" or "0 2".

---

