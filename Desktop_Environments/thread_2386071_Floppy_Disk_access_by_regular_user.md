---
title: "Floppy Disk access by regular user"
date: 2018-02-28
forum: Desktop Environments
---

### Post by peyre on 2018-02-28
This may get big laughs and eyerolls, but I still use floppy disks.  (They have their uses, and I'm always taking little files back and forth to work.  If I put them on a flash drive I'll forget I put them there, but when I find a disk in my work bag, that reminds me--besides, it's too easy to just leave files on a flash drive and having them on floppy prompts me to get them off.)

I'm running the latest version of Xubuntu on an older (~2009) desktop with a built-in floppy drive.  I can mount and read the floppy the same way I would a flash drive or optical disk, but with a floppy disk it gives me only read access.  In order to write to the disk (even, of course, to move files off or delete them), I have a launcher set to run ```
gksudo thunar
``` and start in ```
/media/floppy0
```, and that works fine, but it's a little awkward.  Is there a way to get the system to mount it with rwx access for me?  I've tried going into Users and Groups, and give myself User Privileges for floppy drives, but that doesn't help (see attached).

[ATTACH=CONFIG]278716[/ATTACH]

---

