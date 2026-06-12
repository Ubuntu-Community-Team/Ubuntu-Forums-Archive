---
title: "Cannot Mount Volume"
date: 2009-01-26
forum: General Help
---

### Post by Tyecom on 2009-01-26
Hi,

I am completely new to Ubuntu and this forum, but I really do need some help.  I have a HP Laptop that hard drive took a crash on me.  I am desperately trying to retrieve files from this drive.  However, when I boot-up with Ubuntu and try to mount the drive, I get a error message that says "Cannot Mount Volume"  "Operation Not Supported Mount is denied because NTFS is marked to be in used".  Can anyone help me with this.  Thank you in advance.

---

### Post by cariboo on 2009-01-26
The best way to fix the problem is to boot into the Windows recovery console and run:

```
chkdsk /r
```

and restart windows. If you don't have a windows partition you can install the NTFSprogs package and use ntfsfix to try and solve the problem. You can use Systeem-->Administration-->Synaptic package manager to install ntfsprogs.

Jim

---

### Post by Crafty Kisses on 2009-01-26
Try rebooting your machine and running this command:
```
sudo mount -a
```
If that doesn't work, please post the results of these commands:
```
sudo fdisk -l
df -h
```

---

### Post by Tyecom on 2009-01-26
Cariboo907,

How can I boot up into the Window Console when the Hard is not working...never done it before.

CodeName,

I'll also try your suggestion and will get back to you in a few.  Thank you both for responding, I really appreciate it.

---

### Post by artsci2 on 2009-02-07
I'm having similar problems. I believe the windows drive has a bad virus also and hope to just recover my data files. 

the command suggested by the system: sudo mount -t ntfs-3g /dev/sda1/media/DRV4_VOL1 -o force did not work 
[IMG]file:///home/john/force1.png[/IMG]


[IMG]file:///home/john/window1[IMG]
[IMG]file:///home/john/window2.png[IMG]
[IMG]file:///home/john/sudo_mount-f_and_df-h.png[IMG]

---

### Post by taurus on 2009-02-07
> **artsci2 said:**
> I'm having similar problems. I believe the windows drive has a bad virus also and hope to just recover my data files. 

the command suggested by the system: sudo mount -t ntfs-3g /dev/sda1/media/DRV4_VOL1 -o force did not work 
[IMG]file:///home/john/force1.png[/IMG]


[IMG]file:///home/john/window1[IMG]
[IMG]file:///home/john/window2.png[IMG]
[IMG]file:///home/john/sudo_mount-f_and_df-h.png[IMG]

You forgot to upload the screenshots.  

Try something like these from a terminal.

```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1  /media/sda1 -o force
df -h
```

---

### Post by artsci2 on 2009-03-28
Thanks for the response.

Where should I look to find  the manuals that will tell me how to upload screenshots?

I have tried to click on the paperclip icon, browsed to the screenshot file, clicked upload.......nothing.

I tried to drag the screenshot into my post. Got the text that inspired ¨forgot to load¨

RE the disk being unacessable I just booted the windows install cd and then canceled the install. Then rebooted into Ubuntu and was able to mount.
Don´t have and don´t want a windows system installed on my computer.

---

