---
title: "Mounting error"
date: 2009-05-20
forum: General Help
---

### Post by doindo on 2009-05-20
Hi guys, I recently put Ubuntu 9.04 on my laptop and have enjoyed using it thus far. Last night however, I messed something up when I screwed around with the settings on my windows partition to try to get it to automatically mount on start-up. Now I can't access my windows partition from Ubuntu x_x.

Whenever I click on the drive under the places folder, an error window comes up that says:

[B]Cannot mount volume.
[/B]Invalid mount option when attempting to mount the volume.

---

### Post by StuartN on 2009-05-20
> **doindo said:**
> Whenever I click on the drive under the places folder, an error window comes up that says:

[B]Cannot mount volume.
[/B]Invalid mount option when attempting to mount the volume.

Did you mess it up from in Windows or in Ubuntu? If you messed it up from Windows then reboot Windows and do a clean shutdown - Ubuntu will not mount an unsafe partition. If you messed it up from Ubuntu then which files have you altered?

---

### Post by doindo on 2009-05-20
I messed it up from Ubuntu under the properties of the partition. I didn't change any files around. If you right click on your mounted device then click properties, then go to the volume tab, and then click on setting, the field that says mount options..... that's what I screwed with :D

---

### Post by doindo on 2009-05-20
Bump.

---

### Post by dspisak on 2009-05-20
Hello. I did the same thing and I cannot get a volume to mount.  Help please.

---

### Post by KhurramM on 2009-05-20
just open the properties and print screen and post this back.

---

### Post by dspisak on 2009-05-21
I corrected the problem.  I installed Storage Device Manager (SDM) and selected the partition in question (sda2).  I then selected the Mount option, mounted the partition, selected Properties/Volume and changed the mount point from /mnt back to /media where it was originally.  Closed Properties.  In SDM I then selected Assistant and set "Allow a user to mount and unmount the file system".  Pressed OK, then Apply, then Close. I rebooted and all is well.

But... there is a problem with the partition's name.  In XP it is "HOME".  In Linux the icon the desktop is "76.2 GB Media" while in Nautilus/File System List View it is /media/sda2.  How can I change the name to "HOME"?  The Rename commands are greyed-out.

Thanks to you all for your tips.

Dan

---

### Post by doindo on 2009-05-22
> **dspisak said:**
> I corrected the problem.  I installed Storage Device Manager (SDM) and selected the partition in question (sda2).  I then selected the Mount option, mounted the partition, selected Properties/Volume and changed the mount point from /mnt back to /media where it was originally.  Closed Properties.  In SDM I then selected Assistant and set "Allow a user to mount and unmount the file system".  Pressed OK, then Apply, then Close. I rebooted and all is well.

But... there is a problem with the partition's name.  In XP it is "HOME".  In Linux the icon the desktop is "76.2 GB Media" while in Nautilus/File System List View it is /media/sda2.  How can I change the name to "HOME"?  The Rename commands are greyed-out.

Thanks to you all for your tips.

Dan

You are ******* amazing..... TY!!!!

---

