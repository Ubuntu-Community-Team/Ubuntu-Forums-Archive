---
title: "RSync Backup Script"
date: 2009-05-02
forum: General Help
---

### Post by zephyrcat on 2009-05-02
I am working on setting up a backup system using a NAS (Drobo) such that I have several snapshots that each appear to have all the files, but only use space to store files. (Think of TimeMachine.)

I followed this tutorial:

[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

and this is the script I am using (run daily with cron):

```
#!/bin/sh
cd /home/thomas/.gvfs/
cd "drobo on droboshare"
cd ThomasM1530/home/
ls
rm -rf backup.3
mv backup.2 backup.3
mv backup.1 backup.2
mv backup.0 backup.1
cp -al backup.0 backup.1
rsync -v -a --delete --exclude=".gvfs" --exclude=".VirtualBox" --exclude=".miro" --exclude=".nautilus" --exclude=".Trash" --exclude="*.iso" --exclude=".dbus" /home/thomas/ backup.0/
touch test.txt
```

Basically, it is supposed to use hard links, such that only files that are changed are recreated and the other ones are just links.

What I have is a bunch of folders (backup.0, backup.1, etc.) that have the folder structure, but none of them have any files in them?

What's wrong?

Thanks!

---

