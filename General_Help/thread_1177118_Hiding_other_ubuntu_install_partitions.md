---
title: "Hiding other ubuntu install partitions"
date: 2009-06-03
forum: General Help
---

### Post by Mikeee on 2009-06-03
Hi guys,

I have installed kubuntu for myself to develop on and I have installed ubuntu on a seperate partition for my little sister to use.

I am not too worried about the state the ubuntu installation gets into because I can just format if it gets screwed up, however I am worried about her screwing my kubuntu partition up because that partition can be accessed via ubuntu.

I would prefer to remove the partition so ubuntu can no longer see it, that way she cant break it. Is this possible, and if so how can I do this? If this is not possible then is there a way I can make it read-only from ubuntu?

Thanks

---

### Post by x33a on 2009-06-03
remove that entry from fstab.

post the output of
```
sudo fdisk -l
cat /etc/fstab
```

---

