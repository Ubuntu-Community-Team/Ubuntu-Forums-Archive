---
title: "Share files with XP"
date: 2005-09-09
forum: Desktop Environments
---

### Post by JKingDev on 2005-09-09
My PC now dual boots to kubuntu (I posted here because its not a KDE specific problem) and XP. The first time I booted linux, I was able to access the XP partition. Now it tells me it cannot mount the device. Is there a reason/fix for this? I also created a 5GB partition specifically for sharing files with XP, and I can access it, but I cannot create a file in it. It tells me access denied, could not write to /data/./textfile. The partition is FAT32, mounted at /data. Can this be fixed? Thnx

---

### Post by JKingDev on 2005-09-09
[QUOTE=JKingDev]My PC now dual boots to kubuntu (I posted here because its not a KDE specific problem) and XP. The first time I booted linux, I was able to access the XP partition. Now it tells me it cannot mount the device. Is there a reason/fix for this? I also created a 5GB partition specifically for sharing files with XP, and I can access it, but I cannot create a file in it. It tells me access denied, could not write to /data/./textfile. The partition is FAT32, mounted at /data. Can this be fixed? Thnx[/QUOTE]
 Anyone? I searched and could not find.

---

### Post by byen on 2005-09-09
[QUOTE=JKingDev]Anyone? I searched and could not find.[/QUOTE]
 Ok. first things first.
1.you can read/write on a FAT32 partition
2.NTFS is read only through Ubuntu 

Now..you can mount them manually or add it to your boot up options so that it auto mounts at bootup. Here is what you need to do:
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

Hope this is what you are looking for. Let us know if you need anything else.Goodluck and Welcome to Ubuntu.

---

### Post by JKingDev on 2005-09-10
[QUOTE=byen]Ok. first things first.
1.you can read/write on a FAT32 partition
2.NTFS is read only through Ubuntu 

Now..you can mount them manually or add it to your boot up options so that it auto mounts at bootup. Here is what you need to do:
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

Hope this is what you are looking for. Let us know if you need anything else.Goodluck and Welcome to Ubuntu.[/QUOTE]
 Thanks for the help. I got the ntfs partition mounted right. The FAT32 partition will mount, but I *still* can't write to it. Any suggestions?

---

### Post by Christoff UK on 2005-09-10
Do you get a specific error when trying to write to it, you might need to use sudo,so 'sudo mv /file-wanting-to-be-moved /destination' to move a file, or you could if you want to do it graphically, type gksudo nautilus , in the run application box, and then move your files.

---

### Post by JKingDev on 2005-09-12
Thanks for all the help. The problem was that it was already being mounted, but with default settings. When I modified fstab, I removed the origional definition, and added the new one. It works now. I can save to existing files. When I create new files, they dont always apear, but it still works. Thnx!

---

