---
title: "rc.local, copy/backup directory on boot?"
date: 2009-05-17
forum: General Help
---

### Post by Gorlist on 2009-05-17
Good day, im trying to figure how to backup a directory (and contents) on boot, to a second partition on the drive. So far ive tried adding the following to rc.local file:

```
sudo -U foobar cp /home/foobar/Desktop/Game\ Takings/ /media/disk/
```

However as you can guess its not working :)

Any suggestions?

---

### Post by Legace on 2009-05-17
Maybe you could try:
```
sudo rsync -av --delete /THIS/IS/SOURCE /THIS/IS/DESTINATION
```

---

### Post by Gorlist on 2009-05-18
Hi, thanks for reply - tried it but again nothing seems happen, almost seems if rc.local is redundant and not executed on start?

---

