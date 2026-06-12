---
title: "Help home directory lost"
date: 2006-10-06
forum: Desktop Environments
---

### Post by abenstex on 2006-10-06
Hi everyone,

i just made something i think i should not have done: Well, i changed the partition size of a ntfs partition in order to have a separate partition for my home directory. Then i changed the mount point of my home directory to this new partition, but now ALL files i had in my home directory are somehow missing. Any ideas where they are?

---

### Post by po0f on 2006-10-06
abenstex,

Unmount your new /home partition, and you should find your files again.  You'll need to move your home folder out of /home after unmounting your new partition, remount it, and then put your home folder back in there.

---

### Post by monktbd on 2006-10-06
unmount the new partition again. your home folder contents should appear again.

then mount the new home partition under something like /newhome (mkdir the newhome directory first) then copy all the contents of the /home folder to the /newhome folder and unmount /newhome and remount it as the new /home again.

edit: heh - too slow, notes to self: type faster ;)

---

### Post by kamazu on 2006-10-06
just unmount your newly mounted homedir by
```
sudo umount /home
```
and everything should be visible again. To shift your data to your new partition, mount it temporarly somewhere else, cp everything, unmount the temp mountpoint and mount /home again.
```
sudo mkdir /mnt/tmp
sudo mount /dev/your_partition /mnt/tmp
cd /home
sudo tar cf - . | (cd /mnt/tmp && sudo tar xBpf -)
sudo umount /mnt/tmp
sudo mount /home
```
I hope this helps

kamazu

edit: I was even slower

---

### Post by abenstex on 2006-10-06
THANKS to all of you for your answers. Gosh, how i hate it when my files disappear :rolleyes:

---

