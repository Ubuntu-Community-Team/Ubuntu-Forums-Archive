---
title: "scripting: help with my while loop"
date: 2009-05-15
forum: General Help
---

### Post by goldfish2 on 2009-05-15
I just need help with the syntax of the WHILE statement... all the other commands are written correctly.  I'm trying to make a simple program to mount my raid.  Every time the "create" fails, I need to do a "remove".  Once it is finally successful I want to run the mount command:

```
while [[ cryptsetup create MyRaid /dev/md0 ]]
do
  cryptsetup remove MyRaid /dev/md0
done

mount /dev/mapper/MyRaid /mnt/raid/
```

The "[[" isn't quite working... how do I make the while statement contingent on the exit status of the cryptsetup create command.

Thanks,
GoldFish

---

