---
title: "Emptying the Trash"
date: 2009-01-22
forum: Desktop Environments
---

### Post by Funky91 on 2009-01-22
How do I empty the trash of my 2nd hdd from the command line. When I try to dismount the drive it asks if I want to empty the trash which is exactly what I want to do. However when I click yes it says only root can do this.

How can I do it as root or empty it from the command line as root?

---

### Post by XanTrax on 2009-01-22
Open a terminal and type

```

cd /media

```

Then, identify the hdd you want to delete stuff from.  Change directory (cd) into that directory.  Then issue

```

ls -al

```

Look for a folder that is prefixed with a . ;  The folder can be called one of few things

.trash
.Trash

For example...look for a prefixed folder with a period and delete that folder (should be the trash folder)

For example:

my second hdd is called disk-2 and I want to delete the trash folder from it...I am showing a live example of what I said to up there..

```

cd /media/
cd disk-2
ls -al 
cd .Trash
sudo rm -rfv *
cd ..
rm -rfv .Trash

```

cd into /media/disk-2
did ls -al to find the .Trash folder
cd into .Trash
delete all of its contents
cd up a directory
delete the .Trash directory


You could also just do rm -rfv .Trash all together

---

