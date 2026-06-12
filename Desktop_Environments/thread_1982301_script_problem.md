---
title: "script problem"
date: 2012-05-18
forum: Desktop Environments
---

### Post by davestevens on 2012-05-18
Xubuntu 12.04.
What is wrong with this script please?

#!/bin/sh
Thunar /media/E0FD-1813/download
mv /home/david/downloads/*.mp3 /media/E0FD-1813/download
umount /media/E0FD-1813
aplay /usr/share/audio/beep_high.wav

media/E0FD-1813 mounts automatically, the file transfer takes place correctly, but then it does not unmount. The final sound line also works correctly. Running the umount command in terminal unmounts volume as expected.
Any help would be greatly apprecioated.

---

### Post by roelforg on 2012-05-18
> **davestevens said:**
> Xubuntu 12.04.
What is wrong with this script please?

#!/bin/sh
Thunar /media/E0FD-1813/download
mv /home/david/downloads/*.mp3 /media/E0FD-1813/download
umount /media/E0FD-1813
aplay /usr/share/audio/beep_high.wav

media/E0FD-1813 mounts automatically, the file transfer takes place correctly, but then it does not unmount. The final sound line also works correctly. Running the umount command in terminal unmounts volume as expected.
Any help would be greatly apprecioated.

```

#!/bin/sh
Thunar /media/E0FD-1813/download
mv /home/david/downloads/*.mp3 /media/E0FD-1813/download
sudo umount /media/E0FD-1813
aplay /usr/share/audio/beep_high.wav

```
I modded the script for you
umount can only be run by root so i prepended sudo, can you try this one?
If this failes, post the error umount puts out.

---

### Post by ksprasad on 2012-05-18
If you dont want to use sudo in script, use udisks utility:
 
udisks --unmount /dev/<diskname>
 
Regards,
ksprasad

---

### Post by davestevens on 2012-05-18
> **ksprasad said:**
> If you dont want to use sudo in script, use udisks utility:
 
udisks --unmount /dev/<diskname>
 
Regards,
ksprasad

udisks gives this error

Device file /media/E0FD-1813 is not a block device: Resource temporarily unavailable

---

### Post by davestevens on 2012-05-18
> **roelforg said:**
> ```

#!/bin/sh
Thunar /media/E0FD-1813/download
mv /home/david/downloads/*.mp3 /media/E0FD-1813/download
sudo umount /media/E0FD-1813
aplay /usr/share/audio/beep_high.wav

```I modded the script for you
umount can only be run by root so i prepended sudo, can you try this one?
If this failes, post the error umount puts out.

I had to run this in terminal otherwise there was no prompt to enter password. Using gksu instead gave a password box pop-up, but it still failed.
If I run the original script in a terminal it works, but it does not work when called by a Thunar configured action.

---

### Post by roelforg on 2012-05-18
> **davestevens said:**
> I had to run this in terminal otherwise there was no prompt to enter password. Using gksu instead gave a password box pop-up, but it still failed.
If I run the original script in a terminal it works, but it does not work when called by a Thunar configured action.

But if it worked, you can disable sudo asking for a pass for umount:
[https://help.ubuntu.com/community/Sudoers#Shutting_Down_From_The_Console_Without_A_Password](https://help.ubuntu.com/community/Sudoers#Shutting_Down_From_The_Console_Without_A_Password)
Will tell you how to do this, it's about /sbin/shutdown but you it shows you the principle for how to do this with other apps (like umount).

---

### Post by LewisTM on 2012-05-18
I assume what you're trying to unmount is some sort of USB drive that was mounted automatically by Xubuntu?

This command should unmount it without needing sudo
```
gvfs-mount -u /media/E0FD-1813
```

Cheers!

---

### Post by aromo on 2012-05-18
> **davestevens said:**
> udisks gives this error

Device file /media/E0FD-1813 is not a block device: Resource temporarily unavailable

What ksprasad suggested was:

   udisks --unmount **/dev**/media/E0FD-1813

By the output, it seems like you forgot the /dev at the beginning.

---

### Post by LewisTM on 2012-05-18
> **aromo said:**
> What ksprasad suggested was:

   udisks --unmount **/dev**/media/E0FD-1813

By the output, it seems like you forgot the /dev at the beginning.
You're on to something
It should be 
```
udisks --unmount /dev/disk/by-uuid/E0FD-1813
```
or if your disk has a label
```
udisks --unmount /dev/disk/by-label/<label>
```
[FONT="Courier New"]gvfs-mount -u[/FONT] does basically the same thing but at a higher level since it also manages network connections.

---

### Post by ksprasad on 2012-05-18
> **davestevens said:**
> udisks gives this error

Device file /media/E0FD-1813 is not a block device: Resource temporarily unavailable

Here you have given /media/E0FD-1813 which is the mount point. But udisks works with the devices present in the /dev directory. Not the mount points. 

Use sudo fdisk -l to find out the device name. For example, if it is sdc, then you have to run:

```
udisks --unmount /dev/sdc
```

Hope this helps.

Regards,
ksprasad

---

### Post by davestevens on 2012-05-18
> **aromo said:**
> What ksprasad suggested was:

   udisks --unmount **/dev**/media/E0FD-1813

By the output, it seems like you forgot the /dev at the beginning.

No, when I included /dev I got a cannot find file error

---

### Post by davestevens on 2012-05-18
> **LewisTM said:**
> I assume what you're trying to unmount is some sort of USB drive that was mounted automatically by Xubuntu?

This command should unmount it without needing sudo
```
gvfs-mount -u /media/E0FD-1813
```Cheers!

This seems to work but desktop drive icon still reports device as mounted. I dont think it is though as Thunar window clears.

---

### Post by davestevens on 2012-05-18
> **ksprasad said:**
> Here you have given /media/E0FD-1813 which is the mount point. But udisks works with the devices present in the /dev directory. Not the mount points. 

Use sudo fdisk -l to find out the device name. For example, if it is sdc, then you have to run:

```
udisks --unmount /dev/sdc
```Hope this helps.

Regards,
ksprasad

Interesting as I was expecting something like /dev/sdb1 but did not know how to identify it. It is shown as sdb. Problem with this solution though is that sd* can change depending on if other devices are mounted I think?

---

### Post by zombifier25 on 2012-05-18
Isn't it easier to just:
```
gvfs-mount -u /media/WHATEVERHERE
```
Or
> **LewisTM said:**
> You're on to something
It should be 
```
udisks --unmount /dev/disk/by-uuid/E0FD-1813
```
or if your disk has a label
```
udisks --unmount /dev/disk/by-label/<label>
```
[FONT="Courier New"]gvfs-mount -u[/FONT] does basically the same thing but at a higher level since it also manages network connections.


EDIT: Nevermind, got ninja'd.

---

### Post by davestevens on 2012-05-18
> **LewisTM said:**
> I assume what you're trying to unmount is some sort of USB drive that was mounted automatically by Xubuntu?

This command should unmount it without needing sudo
```
gvfs-mount -u /media/E0FD-1813
```Cheers!

This one works perfectly so will stick with it. Thanks all.
One last question though... is it possible to bring up a progress bar during the operation similar to that from a 'paste' event?

---

### Post by rai4shu2 on 2012-05-18
For a progress bar, you'd need to have a for loop and something like:

```
zenity --progress --percentage=$COMPLETED --no-cancel
```

I'm not sure how pretty it would look, as I've never tried something like that.

---

