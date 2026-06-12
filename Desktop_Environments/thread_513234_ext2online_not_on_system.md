---
title: "ext2online not on system"
date: 2007-07-30
forum: Desktop Environments
---

### Post by mohnkern on 2007-07-30
I've been slowly migrating my system over to lvm, and up until now, have been unmounting logical volumes before resizing them.

However, I'd like to do this without unmounting them, but when I type ext2online it's not to be found.

Anyone know what package ext2online is installed with?

---

### Post by dreadlord_chris on 2007-07-30
it's in the **ext2resize** package
```

chris@HAL421:~$ ext2online
The program 'ext2online' is currently not installed.  You can install it by typing:
sudo apt-get install ext2resize
Make sure you have the 'universe' component enabled
bash: ext2online: command not found

```

gotta love that command-not-found helper utility....

---

