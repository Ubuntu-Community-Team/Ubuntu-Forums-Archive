---
title: "Symlinks disappeared"
date: 2013-03-13
forum: Desktop Environments
---

### Post by djeyewater on 2013-03-13
I have a folder with program folders installed in it and symlinks to these program folders, e.g. php maps to php-5.4.9

This has been working fine for quite a while, but today these symlinks just disappeared! All the folders are still there, but the symlinks are gone.

I did install some updates earlier today, I'm not sure if that would have anything to do with it?

---

### Post by schragge on 2013-03-13
If those links were somewhere under */usr/lib/* then no wonder they disappeared: anything there isn't supposed to be changed by you and may be overwritten on upgrades.

---

### Post by djeyewater on 2013-03-13
They were all in a folder inside my $HOME directory. Both the folders and symlinks were located in the same directory.

---

### Post by djeyewater on 2013-03-14
My system seems pretty messed up (within my home folder). Only thing I can think of is that I must have done something to recursively delete all symlinks. I was using rm the other day to delete some old logs and it is possible I made a typo somewhere and deleted all the symlinks.

Does anyone know what command would be used with rm to recursively delete all symlinks?

---

### Post by schragge on 2013-03-14
Well, it's not exactly using rm, though ```
find -type l -delete
```

---

### Post by djeyewater on 2013-03-14
Hmmmm... I just looked to find the script I wrote that I thought could have caused this, and it has disappeared, along with all the zipped archives it created, and the log files it deleted are still there.

Now I check, it appears that everything I did on that day has not been saved (as well as the symlinks being deleted). I do run Ubuntu in a VM using VMWare, though I was under the impression that it saves changes to disk as you make them.

Edit: I have a good idea what I must have done now. I sync most of the folders in my home dir via FTP to the host machine, and I must have synced the wrong way. DAMN ME!

---

