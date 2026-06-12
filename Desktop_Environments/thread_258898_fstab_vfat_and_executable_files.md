---
title: "fstab vfat and executable files"
date: 2006-09-16
forum: Desktop Environments
---

### Post by jbm222 on 2006-09-16
I currently have my computer setup to dual boot Ubuntu/XP.  Unfortunately I need XP for about 3 programs for school... I only have to boot into it about once every two weeks and it only cost about 10$ from school, so I can't complain too much.

But anyway, I would like to be able to store some programs on the FAT32 shared data partition that I can execute under linux.  What does my fstab entry for the partition need to look like to do that?

When i run "ls -o" on a directory in that partition, it shows rwx permissions for all users, but then gives me permission errors when I actually try to execute something.  So I'm assuming the key is in the umask setting in /etc/fstab, but i can't figure out what it should be.

Oh, btw, the current entry that is NOT giving me the results i want is:
```

/dev/hda3   /home/brian/data vfat   umask=0000,user 0   0

```

---

