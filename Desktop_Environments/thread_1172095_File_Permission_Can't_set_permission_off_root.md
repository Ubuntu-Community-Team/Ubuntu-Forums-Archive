---
title: "File Permission: Can't set permission off root"
date: 2009-05-28
forum: Desktop Environments
---

### Post by FirstByté on 2009-05-28
I have a NTFS drive I share with my Ubuntu. I actually dual-boot. I just discovered that whenever I try to modify or make changes to files I copy from my Ubuntu [ext3 folders] to the NTFS folders, it sets permission strictly to root. How ever I try reverting the ownership and permission it wouldn't change... It stays as '**root**'

I started noticing this on my Ubuntu 9.04 Jaunty.

I've tried

```

myParentfolder$ sudo chmod a+rwx -R /[COLOR="Red"]myNaughtyFolder
[/COLOR]
```

Even using
```


myParentfolder$ sudo nautilus


```

No good. Is there something I'm doing wrong? I tried copying files to my thumb drive, the permission is my user's not 'root'

**NOTE: If this a repeated post please feel free to notify me and delete**

---

### Post by mcduck on 2009-05-28
You can't change file/directory permissions on FAT/NTFS drives, as those file system's simply don't support Unix-style permissions and ownerships.

For FAT/NTFS drives all permissions are set for the whole drive at mount time.

---

### Post by FirstByté on 2009-06-02
Many thanks much mcduck.:popcorn:

I guess I now understand it. Baseline: I'm happy I still can access the file from Windows. I initially thought it was as a result of my hibernating my Windows.

---

### Post by mcduck on 2009-06-02
You can access the data from Ubuntu a well, you just need to configure the drive in /etc/fstab to mount automatically with correct permissions.

See this guide for details: [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by Bert Mariën on 2009-06-02
As I experienced, every file on a NTFS drive is regarded as "root" when accessing it from a Linux distro.
You can not change it. Just live with it.:popcorn:

---

