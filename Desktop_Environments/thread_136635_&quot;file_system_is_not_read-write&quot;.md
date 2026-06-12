---
title: "&quot;file system is not read-write&quot;"
date: 2006-02-26
forum: Desktop Environments
---

### Post by davedaveh on 2006-02-26
Ooops--
My / file system seems to be correctly notated in /etc/fstab (rw), but I cannot get very far in 5.10 either using sudo or root prompt.  I cannot change any files even if I knew how to change them because "file system is not read-write".  Short of reinstalling, what can I do?
I can get user prompt, or root promp if I want, though.
I cannot copy and paste the info to you because I can't get online with it now.  Can't startx either.

Thanks for suggestions.

---

### Post by Ramses de Norre on 2006-02-26
Maybe there is something weird going on with the permissions, check the permissions of the files you want to change.
Are you sure your fstab line is correct?
Did you do any unusual changes to the filesystem setup??

---

### Post by joehill on 2006-02-26
This may be a shot in the dark, but I had a problem a while back where I couldn't r, w, or x anything, and it turned out that an incomplete checkinstall had changed / to 700, and all I had to do was do a recover boot and type "chmod 755 /".  That fixed my problem.

---

### Post by davedaveh on 2006-02-26
chmod 755 / had no effect on my read-only file system.

Thanks for helping, but I think the only way is a reinstall.

---

### Post by cwaldbieser on 2006-02-26
[QUOTE=davedaveh]chmod 755 / had no effect on my read-only file system.

Thanks for helping, but I think the only way is a reinstall.[/QUOTE]
Did you try remounting the partition as rw?
```

$ sudo mount -o remount,rw /

```

---

