---
title: "Trouble with mount"
date: 2006-02-27
forum: Desktop Environments
---

### Post by Princey on 2006-02-27
Hi:

I went the easy way to mount my windows drive (NTFS) on my new comp using the system control panel. I tried mounting it in my home directory but after having problems on reboot, I had to remove it. Now, it refuses to mount in the /mnt folder as the folder I created in my home directory to house the drive (DRIVE F) won't get deleted. I keep getting an error message saying that the folder is already mounted. Any advice on how to delete the folder so I can go the usual way of mounting the NTFS where it belongs?

---

### Post by Sutekh on 2006-02-28
It won't let you delete the folder because the Windows partition is still mounted I imagine.  

You will have to unmount the partition before you can delete that folder in your home.

Do you know the device name of the partition?  hda1? sda1? etc?

If you are unsure, just type **mount** in a terminal window to see whats mounted and where.  Then you can use the command **umount** to un-mount the NTFS partition.

Here's what I have on my system
```
user@ubuntu:~$ mount
...
**/dev/sda1** on **/mnt/winxp** type **ntfs** (rw,nls=utf8,umask=0222)
...
user@ubuntu:~$

```So I know my NTFS partition is located in /dev/sda1.  I can then use the following code to un-mount the partition, so I can remove the mount folder
```
sudo umount **/dev/sda1**
sudo rmdir **/mnt/winxp**
```Obviusly you will have to replace the **/dev/sda1** with the correct location for your NTFS partition, and the **/mnt/winxp** with the name of the folder in your home directory.

---

### Post by Princey on 2006-02-28
Thanks a lot Sutekh for the advice. I'm at work right now and will get to it as soon as I get home. I'll let you know how it went. Mucho gracias.:D

Edit: Forgot I could log on via vnc to my home machine. Did it and it worked fine. Thanks for the help.

---

