---
title: "Conky + diskiograph with 'disk by id' or 'uuid'??"
date: 2011-01-02
forum: Desktop Environments
---

### Post by teeedubb on 2011-01-02
Hey all

Ive been setting up conky (it so customizable, its great!!) and id like to show a 'disk io graph' for my hdd's with the diskiograph option. Everything works fine if I use the line:

```
${diskiograph /dev/sd* 25, 000000 7f8ed3}
```everything fine. If I use:

```
${diskiograph /dev/disk/by-id/scsi-SATA* 25, 000000 7f8ed3}
```nothing displays in the graph box.

Just wondering if theres any way for conky to use 'disk by id' or 'uuid' so I dont have to use /dev/sd* as the naming isnt persistent.

Any help is greatly appreciated!

---

