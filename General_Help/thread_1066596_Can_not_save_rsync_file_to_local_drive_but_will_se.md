---
title: "Can not save rsync file to local drive but will send to 2nd drive ok"
date: 2009-02-11
forum: General Help
---

### Post by sofasurfer on 2009-02-11
I have a seperate hard drive that I will use for backups.

To backup my system I can run this command...
```

rsync -av  / --delete --exclude=media/* --exclude=mnt/* --exclude=cdrom/* --exclude=/root/.local/share/Trash* --exclude=daryl/Desktop/* --exclude=daryl/.wine --exclude=daryl/.miro /media/disk/backup/system-restoration/backup-files/rsync_file_system

```
and everything works fine.

But for practice I will try running rsync and save my backup to my working systems /home directory by running this command...
```

 rsync -av  / --delete --exclude=media/* --exclude=mnt/* --exclude=cdrom/* --exclude=/root/.local/share/Trash* --exclude=daryl/Desktop/* --exclude=daryl/.wine --exclude=daryl/.miro /home/rsync_file_system

```

But this is the message I get...
```

sending incremental file list
rsync: mkdir "/home/rsync_file_system" failed: Permission denied (13)
rsync error: error in file IO (code 11) at main.c(594) [receiver=3.0.3]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(635) [sender=3.0.3]

```
 
What am I doing wrong?

---

### Post by sofasurfer on 2009-02-11
I mean, if I can save it to my 2nd drive without being root, why would I need to be root (according to the message) to save it to my working drive?

---

### Post by sofasurfer on 2009-02-12
Never mind. I have used my system for so long as the only user on the system and I always think of /home as "all mine". /home is owned by root. That was my problem. Soory for not thinking. I don't blame you's for not answering.

---

