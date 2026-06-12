---
title: "Loading Windows XP Partition in Virtual Box: Out of Memory While Making .vmdk"
date: 2009-01-05
forum: General Help
---

### Post by kaoskorruption on 2009-01-05
I have been following this guide:

[http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

When I try to do part 2 of step 2, I get this:

```
chris@Phantom:~$ VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinHD.vmdk -rawdisk /dev/sda3 -partitions 2 -relative -register
VirtualBox Command Line Management Interface Version 2.0.4_OSE
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

Out of memory allocating the partition descriptor for '/dev/sda3'
The raw disk vmdk file was not created
chris@Phantom:~$ 

```

I have absolutely no idea what to do.

---

### Post by Johnny B on 2009-01-27
i just ran into this problem myself,
you need to refer to your windows partition on /dev/sda3 as:
 /dev/sda -partitions 3
the correct code, in your case would be:
```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinHD.vmdk -rawdisk /dev/sda -partitions 3 -relative -register
```

---

