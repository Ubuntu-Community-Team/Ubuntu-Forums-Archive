---
title: "How did mount read-only option get in my fstab?"
date: 2009-06-05
forum: General Help
---

### Post by ad_267 on 2009-06-05
I booted up my Ubuntu recently and saw something about errors in my file system and it looked like they were being sorted out, but when I went to log in from GDM I got a message:
```
Failed to initialize account for user adam: NT_STATUS_ACCESS_DENIED
```

I had an error about my session lasting less than 10 seconds and my ~/.xsession-errors said:
```
mkdtemp: private.socket dir: Read-only file system
```

Then I had a screen saying something about being unable to start X. So I rebooted into Kubuntu 9.10 and did an fsck on the drive and everything seemed fine. Booted into Ubuntu, same thing again.

The NT_STATUS_ACCESS_DENIED error looked like a Samba problem, so I tried removing samba and libpam-smbpass, but got an error about a read only file system. I tried remounting the root partition but got this error:
```
EXT4fs error. Abort forced by user. Block device is write-protected, mounting read only
```

I had a look at my /etc/fstab and saw the line to mount my root partition had been modified and had something like "error read-only" added. I can't remember what the exact syntax was though. I removed that part and now everything's working fine.

Anyone know what happened there? Should I be worried?

---

### Post by dcstar on 2009-06-05
> **ad_267 said:**
> I booted up my Ubuntu recently and saw something about errors in my file system and it looked like they were being sorted out, but when I went to log in from GDM I got a message:
.........
I had a look at my /etc/fstab and saw the line to mount my root partition had been modified and had something like "error read-only" added. I can't remember what the exact syntax was though. I removed that part and now everything's working fine.

Anyone know what happened there? Should I be worried?

YES!, you have a filesystem with ERRORS on it and **you** are making the errors worse by mounting it RW.

Fix the actual problem, not the thing that prevents the problem from getting worse.

---

### Post by ad_267 on 2009-06-05
How do I fix the problem? Running fsck doesn't pick anything up. I don't have anything important on there so if it fails I'll just get a new drive. I also checked /var/log/messages and didn't see anything that looked important.

I got a bit confused in my first post too. After getting the problem logging in the first time, I rebooted the computer and a menu came up with a few options, one was to do a file system check so I selected this and fsck ran and repaired a few things. So I'm just wondering why the file system was still mounted read-only. Is it likely my hard drive is failing? Or is this just normal corruption of the file system which I shouldn't worry too much more about.

---

### Post by el_fela on 2009-10-20
Its a samba authentication related problem. I know cause im working on it.

---

