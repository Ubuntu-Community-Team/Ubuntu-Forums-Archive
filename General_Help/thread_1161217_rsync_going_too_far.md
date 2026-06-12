---
title: "rsync going too far"
date: 2009-05-16
forum: General Help
---

### Post by zob on 2009-05-16
Hi.
I'm trying to make a backup of my /home folder (and subfolders of course). I using rsync and the following is the command:
```
sudo rsync -vrtplz --progress --stats --delete --backup --backup-dir=/media/LinuxBackExt3/$HOME-`date +%A` $Home/ /media/LinuxBackExt3/aktuel_backup
```

The first thing it does is fine. I actually makes a backup in the place I intended and in the way I intended. But then it just keeps on, making backups of, well.. of everything. The whole filesystem including mounted drives. Until I tell it to stop manually, that is. Because there wouldn't be space for everything anyway.

But the command seems to be fine - nothing wrong with that. Or what?

The other possibility, I guess, would be that somehow my /home folders links rsync back to my root folder. But I can't see how. There are no disks mounted in my /home folder. So how would that happen?

Any help? Thanks.

---

### Post by dcstar on 2009-05-16
> **zob said:**
> Hi.
I'm trying to make a backup of my /home folder (and subfolders of course). I using rsync and the following is the command:
```
sudo rsync -vrtplz --progress --stats --delete --backup --backup-dir=/media/LinuxBackExt3/$HOME-`date +%A` $Home/ /media/LinuxBackExt3/aktuel_backup
```

The first thing it does is fine. I actually makes a backup in the place I intended and in the way I intended. But then it just keeps on, making backups of, well.. of everything. The whole filesystem including mounted drives. Until I tell it to stop manually, that is. Because there wouldn't be space for everything anyway.

But the command seems to be fine - nothing wrong with that. Or what?

The other possibility, I guess, would be that somehow my /home folders links rsync back to my root folder. But I can't see how. There are no disks mounted in my /home folder. So how would that happen?

Any help? Thanks.

There is no such thing as "$Home" (it is $HOME) so it ends up being "/" and will do exactly as you describe.

---

### Post by zob on 2009-05-17
Thanks. You were right.

---

