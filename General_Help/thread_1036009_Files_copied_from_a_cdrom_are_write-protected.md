---
title: "Files copied from a cdrom are write-protected"
date: 2009-01-10
forum: General Help
---

### Post by bd@cb8be8510 on 2009-01-10
When I copy files from a cdrom to my disc, the files copied are write-protected. Can I set a switch such that the files copied are no longer write-protected by default? This feature is rather annoying when you have to restore a lot of backupped-data, then you need to manually change the attributes of the files afterwards.

---

### Post by KeyserSoze93 on 2009-01-10
Maybe you need to set some kind of masking flag in your /etc/fstab for the cdrom mount points. Cam you post your fstab?

---

### Post by Slim Odds on 2009-01-10
By default, Ubuntu alaises cp to "cp -p". This means "preserve file attributes".

You could use:```
command cp <whatevery you used before>
```

To copy without preserving attributes.

BTW, all files on a CD-ROM or DVD-ROM will have the Read Only attribute.

---

### Post by bd@cb8be8510 on 2009-01-10
Ok, but then you'll need to copy the files using the commandline. But I prefer rather Nautilus. I would be nice to have this feature in the preferences-dialog of Nautilus.

---

### Post by Slim Odds on 2009-01-10
> **bd@cb8be8510 said:**
> Ok, but then you'll need to copy the files using the commandline. But I prefer rather Nautilus. I would be nice to have this feature in the preferences-dialog of Nautilus.

I didn't see any option in Nautilus to do this, but changing the attribute to writable is not hard. Just select all the files, right-click and go to the permissions tab.

With Ubuntu (and really, linux in general) there are tons of ways to automate the process. Sometimes the command line is the best.

But whatever.....

---

