---
title: "Unable to unmount network ftp server folder"
date: 2009-06-19
forum: General Help
---

### Post by kehon on 2009-06-19
i used nautilus to connect to an ftp server and another ftp server so that i could copie one to the other well it never finished in fact it got hung and had to killall nautilus because desktop icons disaperred and couldnt right click on desktop along with background gone so i fixed that but now i cant unmount or view that folder one of them was able to be unmounted but the other works with filezilla but not nautilus to well in facts its slow so i need to unmount it how can i umount the last folder

---

### Post by MaxIBoy on 2009-06-19
Look at the file /etc/mtab. You should see a line that describes the device of the mounted directory, as well as the mount point. The format for each line is 
```
<device> <mountpoint> <mount options> <some numbers that I don't know what they do>
```

Unmount it using this command: ```
sudo umount <mountpoint> #umount, not unmount
```
So for example, if the mount-point was /media/network, you'd type "sudo umount /media/network" to unmount it.
If that doesn't work, use the "-f" flag to force it, as in 
 ```
sudo umount -f <mountpoint> 
```

---

### Post by kehon on 2009-06-19
actually couldnt find in /media or in system manager that shows mounted filesystems think i'll restart later and that should clear things up

---

