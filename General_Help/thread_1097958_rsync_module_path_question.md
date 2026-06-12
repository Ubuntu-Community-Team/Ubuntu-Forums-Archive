---
title: "rsync module path question"
date: 2009-03-16
forum: General Help
---

### Post by malfist on 2009-03-16
I want to create an rsync module that saves the files in ~/backup because I'll have multiple users backing up to the same server and I don't want the backups mixing together and causing problems.

I've tried setting the path ~/backup in the rsync conf but it fails with @ERROR chroot failed, and only works if I type out the full path (i.e. /home/x/backup).

How can I do this?

---

### Post by fjgaude on 2009-03-16
I'm not sure I understand your problem. I use this to backup my database:

```
sudo rsync -r -t -p -o -g --progress --delete /home/raid/ /media/backup/raid/
```

Now it should be clear that you have to go from a source to a destination.

---

### Post by malfist on 2009-03-16
I think I need to explain myself better. I'm backing up from a window servers, as you may know, all root directories start with a single letter directory. If I have all the servers back up to /home/x/backups I would run into a problem when the servers have same named directories (example, servers often have a C:\inetpub) which could cause havoc.

I'm using a windows rewrite of the rsync algorithm and it doesn't support everything the normal rsync does, for example, it doesn't support backing up to something like user@server:/home/user/backup, it only supports backing up to rsync://user:pw@server/module (and password files).

I've tried adding
use chroot = no
munge symlinks = no

but rsync daemon complains that the ~/backup does not exist when trying to backup using a user that does have a ~/backup

---

### Post by fjgaude on 2009-03-16
I don't do Windows anymore...

Maybe someone else here will know how to help you. Sorry!

---

### Post by malfist on 2009-03-16
But the problem isn't with the windows side right now, the problem is with rsync's handling of the '~' symlink.

---

### Post by fjgaude on 2009-03-16
The only thing to suggest is to study the man pages and notice what rsync can and cannot do... I have no experience with it crossing sym links... just down the LAN and drive to drive.

You aren't trying to use it remote to remote, eh?

---

### Post by malfist on 2009-03-16
No, just from local to remote in the standard client/server relationship. I fould something on the bug tracker about it not being able to follow relative paths. It's supposed to be fixed post 3.0.0 but I'm running 8.04 and it only has 2.6.9. Hopefully an update will fix it. The rsyncd man page says nothing about it, I've read it several times today.

---

### Post by fjgaude on 2009-03-17
Hope you find out what's wrong... I'm running 2.6.27-11, waiting for 9.04 next month. <smile>

---

### Post by fieroboom on 2009-03-17
> **malfist said:**
> I think I need to explain myself better. I'm backing up from a window servers, as you may know, all root directories start with a single letter directory. If I have all the servers back up to /home/x/backups I would run into a problem when the servers have same named directories (example, servers often have a C:\inetpub) which could cause havoc.

I'm using a windows rewrite of the rsync algorithm and it doesn't support everything the normal rsync does, for example, it doesn't support backing up to something like user@server:/home/user/backup, it only supports backing up to rsync://user:pw@server/module (and password files).

I've tried adding
use chroot = no
munge symlinks = no

but rsync daemon complains that the ~/backup does not exist when trying to backup using a user that does have a ~/backup

Correct me if I'm wrong, but I believe rsync requires a fully qualified path unless you specify the relative path switch with -R.
Check out the options on the man page:  [http://www.manpagez.com/man/1/rsync/](http://www.manpagez.com/man/1/rsync/)
Scroll down till you see "Options Summary", and the relative switch is about the 8th one down. Also, below that section is the "Options" section, which contains a detailed breakdown of the -R switch.

If this isn't really what you're looking for, then you might want to consider not running it as a daemon, and instead run it in crontab for each server you're backing up. This way you have complete control over each backup, instead of a global config.
Let me know if I can help more. :D
-Paul

---

