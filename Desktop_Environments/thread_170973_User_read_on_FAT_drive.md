---
title: "User read on FAT drive"
date: 2006-05-05
forum: Desktop Environments
---

### Post by Atholm on 2006-05-05
Aloha.

I have a problem, i have mountet a vfat drive, and can find read and write in file browser, because i'm the owner of the drive.
My problem is i use FTPserver an users don't have permission to read to drive so they can't enter the drive on my server.
What shall i do, i guess i have to put something funky in the fstab file but what :-D

Thanks

---

### Post by tonyr on 2006-05-05
Here's how I do it in fstab:
```

/dev/hda8       /media/hda8     vfat    defaults,umask=0        0       0

```

Some people say to use **umask=0000**, which is the correct **octal**
syntax, but mine has always worked for me.  Use your own **device** and 
**mount-point**, of course.

From a terminal command line, 
```

sudo umount <device>
sudo mount -t vfat -o defaults,umask=0 <device> <mount-point>

```

---

### Post by matthewstory on 2006-05-05
This is untested but shouldn't you be able to do something like this:

sudo addgroup editvfat
sudo adduser ftpuser editvfat
sudo cd /media
sudo chmod -R 775 VFAT
sudo chgrp -R editvfat VFAT

The only thing about this is that you might have to do it everytime the drive is mounted, but then you could just script the last 2 lines or so and have it run on mounting of the drive.

---

