---
title: "Deleting system file"
date: 2009-04-23
forum: General Help
---

### Post by icedsalmon on 2009-04-23
I'm trying to delete auto_exposer in my webcam file it keeps ruining my brightness as its auto adjusting it badly.
The file is under /sys/module/sn9c20x/parameters/auto_exposer
I have tried logging in as root, using rm -f and changing the permissions but all I get is permission denied :confused:
Is there anyway to delete it?
I'm using Ubuntu 9.04 and the webcam is a vx-6000 which is nearly working :)

Thanks

---

### Post by oldos2er on 2009-04-23
```
sudo rm /sys/module/sn9c20x/parameters/auto_exposer

```

---

