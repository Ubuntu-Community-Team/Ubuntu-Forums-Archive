---
title: "Nautilus copy from SSH share - preserve attributes?"
date: 2008-04-08
forum: Desktop Environments
---

### Post by Soundman2 on 2008-04-08
Greetings.

Using Gnome's Places->Connect to Server via SSH protocol, one can browse and copy files on the remote machine via Nautilus.

The Problem: The modification timestamp is not preserved when files are copied via drag'n'drop in Nautilus over the ssh share.  The copied files get the current time instead!  This does not occur when copying files among local drives (nor, I believe vie SMB or NFS mounts) - in those cases, Nautilus preserves attributes.

I know that **scp -p** option will preserve attributes on the command line like this:
```
scp -r -p remotehost:/some/directory .
```

But how to get Nautilus to do this when it copies files? :confused:

Thanks,
Soundman2

---

### Post by linux4pc on 2008-04-30
i have the same question, hope someone can give me a hand.
even copy files from usb drive, it won't preserve the date stamp of files.

thanks in advance.

---

### Post by Kumera on 2008-05-01
I am also having a real problem with this.  In Ubuntu 7, copied or moved files would retain their original attributes, but in Ubuntu 8, the date/time property is changed to the date of the copy, and the actual editing or creation date is lost. :(

---

### Post by cest on 2008-05-05
I have the same problem... with ssh but also with local files...

---

