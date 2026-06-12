---
title: "Mount name for a USB disk"
date: 2005-08-11
forum: Desktop Environments
---

### Post by gsasha on 2005-08-11
I have an external USB disk with two partitions, one FAT32 and one ReiserFS, with labels like MAXTOR and MAXTOR_LNX.

Once upon a time, I was a Mandrake user. Mandrake handled the disk in the following way: as I plugged it in, the disk appeared as /mnt/MAXTOR and /mnt/MAXTOR_LNX.

Now, in Kubuntu 5.04, it works a bit dumb to my opinion: the device appears as /media/sda1 and /media/sda2. On desktop (due to KDE if I understand correctly), it appears as media:/MAXTOR, but that name is accessible only through the KDE file manager, not from the shell.

I have a script that needs to access the drive contents automatically, but it wouldn't work correctly with the /media/sda* names, since I have several different USB storage devices and thus the naming would not be stable.

Is there a way to get the same behavior as in Mandrake (i.e. having the device named /media/MAXTOR instead of /media/sda1)?

---

### Post by Jade Robbins on 2005-08-11
[QUOTE=gsasha]I have an external USB disk with two partitions, one FAT32 and one ReiserFS, with labels like MAXTOR and MAXTOR_LNX.

Once upon a time, I was a Mandrake user. Mandrake handled the disk in the following way: as I plugged it in, the disk appeared as /mnt/MAXTOR and /mnt/MAXTOR_LNX.

Now, in Kubuntu 5.04, it works a bit dumb to my opinion: the device appears as /media/sda1 and /media/sda2. On desktop (due to KDE if I understand correctly), it appears as media:/MAXTOR, but that name is accessible only through the KDE file manager, not from the shell.

I have a script that needs to access the drive contents automatically, but it wouldn't work correctly with the /media/sda* names, since I have several different USB storage devices and thus the naming would not be stable.

Is there a way to get the same behavior as in Mandrake (i.e. having the device named /media/MAXTOR instead of /media/sda1)?[/QUOTE]
 Please read the rules for this forum, it is not the place to ask questions. I don't know the answer to your question, but you would have better luck in a different forum.

---

### Post by kassetra on 2005-08-11
[QUOTE=gsasha]I have an external USB disk with two partitions, one FAT32 and one ReiserFS, with labels like MAXTOR and MAXTOR_LNX.

Once upon a time, I was a Mandrake user. Mandrake handled the disk in the following way: as I plugged it in, the disk appeared as /mnt/MAXTOR and /mnt/MAXTOR_LNX.

Now, in Kubuntu 5.04, it works a bit dumb to my opinion: the device appears as /media/sda1 and /media/sda2. On desktop (due to KDE if I understand correctly), it appears as media:/MAXTOR, but that name is accessible only through the KDE file manager, not from the shell.

I have a script that needs to access the drive contents automatically, but it wouldn't work correctly with the /media/sda* names, since I have several different USB storage devices and thus the naming would not be stable.

Is there a way to get the same behavior as in Mandrake (i.e. having the device named /media/MAXTOR instead of /media/sda1)?[/QUOTE]

you could always make symbolic links for each device... I'm not familiar with how KDE does it, so I couldn't tell you exactly why you're not getting the special /media names... but I will move this into the KDE forum, maybe someone there can give you more info.  :)

---

