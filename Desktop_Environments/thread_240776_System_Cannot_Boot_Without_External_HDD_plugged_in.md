---
title: "System Cannot Boot Without External HDD plugged in"
date: 2006-08-21
forum: Desktop Environments
---

### Post by TheMono on 2006-08-21
The title pretty much says it all. I can't figure out how to make my computer boot without the external hard drive plugged in. 

I recently created another partition, formatted ReiserFS, on the external, and now when the system boots without this plugged in, it reaches the "checking all file systems" stage, then announces that it cannot find /dev/sda5 (the Reiser Partition, which it cannot find for obvious reasons), and dumps me to a terminal.

My fstab line reads:

/dev/sda5	/home/daniel/music	reiserfs	nodev,nosuid,noauto,user	0	2 # My Music

I've searched the forums and can't find anything on this, though I imagine this must be reasonably common?

---

### Post by waldschm on 2006-08-21
backup your fstab file:

```
sudo cp /etc/fstab /etc/fstab_backup
```

Then try simply deleting the line for the external out of your fstab file. If it is an external, removable device, you don't need an fstab entry for it.

---

