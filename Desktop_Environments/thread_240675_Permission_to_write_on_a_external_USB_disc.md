---
title: "Permission to write on a external USB disc"
date: 2006-08-21
forum: Desktop Environments
---

### Post by bengtfalke on 2006-08-21
I can see the external USB disc and I can go up and down in the filesystem on it. However I do only hav read permisson on it.

If I go to /media and try chmod a+w usbdisk it replies: media is only readable.....

Help needed urgently as I need to save sm info on my comp before a fresh install with Dapper.....  Windows partions will disapear after this.

Regards/falke

---

### Post by halfvolle melk on 2006-08-21
What file system does the usbdisk have?

---

### Post by bengtfalke on 2006-08-21
I think it is FAT but I have also tried with a Linux formated one... same result  ;o(

---

### Post by waldschm on 2006-08-21
have you tried manually unmounting and remounting the disk using the umount and mount commands?

---

### Post by bengtfalke on 2006-08-21
Can you please provide me with the correct command?

---

### Post by waldschm on 2006-08-21
for unmounting:

```
sudo umount /media/$folder$
```

where you replace $folder$ with the name of the folder the drive is mounted on.

Then to remount:

```
sudo mount -t vfat /dev/sda1 /media/$folder$
```

again replacing $folder$ with the correct name. /dev/sda1 is the correct device for my external usb hard drive but I'm not sure it will be the same but give it a shot.

---

### Post by gregb49 on 2006-08-22
I have a similar problem. ```
sudo umount /media/usbdisk
``` works fine but ```
sudo mount -t vfat /media/usbdisk
sudo mount /media/usbdisk
sudo mount /dev/sda1
```do not recognise the device. Unpluggin and replugging works, after umount, but feels dangerous. I have owner read write priviledges but cannot give them to a group - I want to access this disk from another computer. I've tried ```
sudo chmod 777 /media/usbdisk
``` but this seems to have no effect. I've also tried changing the permissions using nautilus ```
sudo nautilus
```. I can change the owner permissions but not the group or other permissions. Is there anything els I can try? 

For falke - I have found that shutting down, removng the disk, restarting and then reconnecting the disk gives me owner read write permissions back again when my fiddling has messed everything else up. [BTW. USB disk format is FAT 32]. Greg

---

### Post by waldschm on 2006-08-22
Greg, try setting the read/write permissions at mount time rather than afterwords. For instance mount your drive like this:

pmount -t vfat --umask 007 /media/removable /dev/sda1

Setting the permissions to 770, or adjust the umask accordingly. I believe the group if you use the pmount command is plugdev, and you can add users to this group if you have root access.

---

### Post by gregb49 on 2006-08-22
Thanks waldschm, I've tried that, having umounted the drive, but get the following ```
m10000@m10000-desktop:~$ sudo umount /media/usbdisk
Password:
m10000@m10000-desktop:~$ sudo pmount -t vfat --umask 007 /media/removable /dev/sda1
Error: could not determine real path of the device: No such file or directory
m10000@m10000-desktop:~$ sudo pmount -t vfat --umask 007 /media/usbdisk /dev/sda1
Error: invalid device /media/usbdisk (must be in /dev/)
m10000@m10000-desktop:~$ sudo pmount -t vfat --umask 007 /dev/sda1
m10000@m10000-desktop:~$


```Maybe I don't really understand what these commands are doing. I do have a Linux tome, so will get that out later. There are both an **SDA** and **SDA1** in the /dev/ folder but that doesn't tell me much.

I do now have an sda1 usb disk and the /media/usbdisk has disappeared, but I can only access the disk now in root. Clearly I'm making something happen:shock:  Greg

---

### Post by waldschm on 2006-08-22
Wow, my fault Greg, I think part of the problem is in my last post I got the order switched around a little. First let's clarify things, it looks like you are trying to mount the same device at two separate points? Do you have one external disk with one partition, if so you only need to mount in one place in the /media directory. Secondly, as I said it should be:
mount [device] [mount point]
not the other way around so lets Unmount first:

```
sudo umount /media/whatever
```

Then go ahead and try the normal mount command:

```
sudo mount -t vfat --umask 007 /dev/sda1 /media/whatever
```

Finally, if that doesn't work, unmount again, just like in the first command, then try mounting with pmount(shouldn't need sudo):
```

pmount -t vfat --umask 007 /dev/sda1 /media/whatever
```

hopefully this works better, but say so if you're confused or neither of these works

EDIT: make sure to change the whatever in /media/whatever to the name of the directory where you want to mount the drive, also make sure this directory exists and nothing else is mounted there.

---

### Post by gregb49 on 2006-08-23
Many thanks waldschm. I've had to put this on hold as the latest ubuntu automatic update of X has made my computer unuseable for the time being. [There's a message there somewhere:redface: ]. But I'll return to this as soon as possible as there is good training here for me, and I hope for others who are struggling to read/write to USB disks, plus I need to get on with my accounts that are on this disk. Greg

---

