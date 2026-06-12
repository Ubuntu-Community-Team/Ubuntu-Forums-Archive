---
title: "SWAP Priority Setting"
date: 2005-06-01
forum: Desktop Environments
---

### Post by rms46 on 2005-06-01
At boot time, my ''partition swap'' (256 MB) will get priority "-1" and my ''swapfile'' (512 MB) will get priority "-2" (on an ext3 fs). May I know which priority is higher: -1 or -2?

If my ''swapfile'' has a higher priority; is there a way to switch; i.e. higher priority for the ''partition swap''?

---

### Post by rms46 on 2005-06-01
May I know if this following /etc/fstab will switch the priority?

```

# <file system>   <mount point> <type> <options>                 <dump><pass>
/dev/hda3             none      swap    sw                           0     0
/extra/.swap/swapfile none      swap    sw,pri=0                     0     0

```

---

### Post by rms46 on 2005-06-09
[QUOTE=rms46]May I know if this following /etc/fstab will switch the priority?
```

# <file system>   <mount point> <type> <options>                 <dump><pass>
/dev/hda3             none      swap    sw                           0     0
/extra/.swap/swapfile none      swap    sw,pri=0                     0     0

```[/QUOTE]

/extra/.swap/swapfile would have higher priority! Therefore, /etc/fstab should be:
```

# <file system>   <mount point> <type> <options>                 <dump><pass>
/dev/hda3             none      swap    sw                           0     0
/extra/.swap/swapfile none      swap    sw                           0     0

```

To check the swap:
```

rmsbase:~$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/hda3                               partition       257032  3112    -1
/extra/.swap/swapfile                   file            533496  0       -2

```

---

