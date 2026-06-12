---
title: "desktop partition link"
date: 2010-08-14
forum: Desktop Environments
---

### Post by keylokes on 2010-08-14
so i just installed on Lubuntu on my old laptop.
runs way better now.

i have a separate partition for my documents which is mounted automatically on boot up with "pysdm" . on Ubuntu there is a little icon on the desktop with a link to the partition.

how can i do that in Lubuntu??? its not super important but it would be nice...

any help.?

---

### Post by dagdeniz on 2010-08-14
As far as I know Pcmanfm does not show mounted partitions on desktop even if it's automounted. You can still symlink to the partition so that you can see it on desktop:

```
ln -s -d /path/to/the/partition /home/yourusername/Desktop/partitionwithdocuments
```

(I'm assuming from your post that the partition is still automounted but only not linked on desktop). 

However, the link will still be there when you unmount the partition.

---

