---
title: "fsck failed error on bootup."
date: 2006-05-08
forum: Desktop Environments
---

### Post by equal on 2006-05-08
Hey guys, something very weird is going on with my desktop. It got shut off accidentally a few days ago, and when I tried to boot back up, I got this error during the boot process:

```
* Checking all file systems...
/dev/hda2: recovering journal
fsck.ext3: unable ot set superblock flags on /dev/hda2

*fsck failed. Please repair manually.
```

Do any of you have any idea what this means. Also, any chance of me fixing this without reformatting hda2? I had a lot of stuff on there that I would rather not have to replace. It's still doable, but alternatives are appreciated!

---

### Post by wacole on 2006-05-10
Don't know what this happened, but I've had ubuntu tell me to run a manual fsck and found that the only way it ran to completion (thanks to the advice of another person on this forum) was to boot ubuntu using the appropriate live-cd (I'm running 5.10), bringing up the terminal and then typing:

sudo fsck -y /dev/hda1

where hda1 is the identity of the hard drive that you want to run fsck against. It takes a couple of hours to run on my machine (an old 800mhz AMD) but it does the job.

Hope that helps.

---

### Post by dcstar on 2006-05-11
[http://ubuntuforums.org/showpost.php?p=754634&postcount=2](http://ubuntuforums.org/showpost.php?p=754634&postcount=2)

---

