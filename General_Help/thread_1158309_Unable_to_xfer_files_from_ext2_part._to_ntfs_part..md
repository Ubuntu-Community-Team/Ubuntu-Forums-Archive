---
title: "Unable to xfer files from ext2 part. to ntfs part."
date: 2009-05-13
forum: General Help
---

### Post by us3598 on 2009-05-13
Hey,
stupid question, but I need to xfer a folder from an ext2 partition to an ntfs partition. However, I am on a xubuntu live cd, and it will not give me the option to do so. How can I accomplish this?

---

### Post by us3598 on 2009-05-13
Really, any help would be appreciated.

---

### Post by michy99 on 2009-05-13
What happens when you try to move the folder?

---

### Post by us3598 on 2009-05-13
well, nothing. It lets me click copy, but not paste...really frustrating, lol. And thanks for replying.

---

### Post by stathol on 2009-05-13
Read-write support for NTFS has always been a little spotty in Linux, due to the NTFS being a closed, and undocumented filesystem. There is, however, an NTFS file system driver that supports read-write mode: [NTFS-3G](http://www.ntfs-3g.org/). The NTFS-3G package should be part of the default Ubuntu package, but Xubuntu's live CD may trim that out -- I'm not sure.

Try fetching the ntfs-3g package with your tool of choice (Synaptic, apt-get, aptitude, etc.), and then mount your NTFS partition with:

```
mount -t ntfs-3g /dev/<windows partition> /mnt/<wherever>
```

One caveat: ntfs-3g will not mount the file system in read-write mode if hiberfil.sys is present on the partition (meaning that Windows is currently hibernated to that disk). This is for obvious safety reasons.

If that's the case, the safest thing to do is to boot to Windows, resume the system, and then shut it down instead of hibernating it. You can destroy the hibernation file by adding "-o remove_hiberfile" as an option to the mount command above, but that's obviously not recommended. It's no worse than pulling the power plug on a running Windows system, but it's still not a smart thing to do if you have any alternative.

---

### Post by michy99 on 2009-05-13
Open a terminal (Applications->Accessories->Terminal) and enter

```
gksudo nautilus
```

This will open a nautilus session with root permissions. See if you can move the folder now.

---

### Post by us3598 on 2009-05-13
SWEETNESS...had to apt-get install nautilus, then did the gksudo, and it worked perfectly. THANK YOU!

---

### Post by michy99 on 2009-05-13
OOps.. I didn't catch that you were on xubuntu. Nautilus is the default file manager for Gnome. It probably would have worked with whatever file manager xubuntu uses, but I don't know the name of it. Glad you got it done, anyway.

---

