---
title: "Can't access my main Ubuntu partition"
date: 2005-07-26
forum: Desktop Environments
---

### Post by Azmodan on 2005-07-26
It started when I began to burn a DVD before going to bed.  I started the burning and went away.  Before leaving, I locked the screen.

When I came back, the DVD was completed.  I entered my password to unlock the screen and got a bid "DENIED".  I checked it many times.  I checked CapLocks.  It didn't work.

I pressed ShutDown and instead of a clean shutdown, I got plenty of ext3 errors.  I rebooted but once I got to the login screen and entered my username, I got an "authentification error".

I booted on the LiveCD (writing from it right now) and can't see at all my Ubuntu partition.  The swap partition is in /etc/fstab though.

Does someone have an idea for me to save my data ?  I have a CD burner and a CD/DVD burner.

Thanks

---

### Post by bored2k on 2005-07-26
[QUOTE=Azmodan]It started when I began to burn a DVD before going to bed.  I started the burning and went away.  Before leaving, I locked the screen.

When I came back, the DVD was completed.  I entered my password to unlock the screen and got a bid "DENIED".  I checked it many times.  I checked CapLocks.  It didn't work.

I pressed ShutDown and instead of a clean shutdown, I got plenty of ext3 errors.  I rebooted but once I got to the login screen and entered my username, I got an "authentification error".

I booted on the LiveCD (writing from it right now) and can't see at all my Ubuntu partition.  The swap partition is in /etc/fstab though.

Does someone have an idea for me to save my data ?  I have a CD burner and a CD/DVD burner.

Thanks[/QUOTE]
 Can't you boot to a Ubuntu bash using the Recovery boot ? There you could easily change your passwrd. And for the record, its not recommended in any OS to lock or allow a screensaver to run during the burning of a DVD.

Next time your box "freezes" don't press the Shutdown button, first try and see if pressing Alt+Ctrl+F1 gives you a prompt. If it does, log in and type sudo reboot.

---

### Post by Azmodan on 2005-07-26
Didn't work.  It only gives me I/O errors.  And when I boot, it's not when I enter the password that it fails but when I enter the username...

I'm pretty sure it's corrupted enough that I will have to do a fresh install.  I'm looking forward to a way to save my data before...

---

### Post by bored2k on 2005-07-26
[QUOTE=Azmodan]Didn't work.  It only gives me I/O errors.  And when I boot, it's not when I enter the password that it fails but when I enter the username...

I'm pretty sure it's corrupted enough that I will have to do a fresh install.  I'm looking forward to a way to save my data before...[/QUOTE]
 In case you do reinstall, you don't necessarily need to format the drive. You can simply install over the existing data and it won't delete stuff in your $HOME folder.

---

### Post by Azmodan on 2005-07-26
I've put the install CD in the CD drive and booted.  When I got to the partion step, it offered to erase the disk.

I chose manual partionning.  The help tells me that this version will not overwrite an existing GNU/Linux system...

My $HOME isn't on a separated partition (I chose Ubuntu's default choice...).

Any idea on how to get the LiveCD to see hda1 so I can just burn my data and do a clean install ?

---

### Post by bored2k on 2005-07-26
[QUOTE=Azmodan]I've put the install CD in the CD drive and booted.  When I got to the partion step, it offered to erase the disk.

I chose manual partionning.  The help tells me that this version will not overwrite an existing GNU/Linux system...

My $HOME isn't on a separated partition (I chose Ubuntu's default choice...).

Any idea on how to get the LiveCD to see hda1 so I can just burn my data and do a clean install ?[/QUOTE]
 O.o

Ok, boot the live disc, get in a root terminal and type
```
fdisk -l
```There you should see something similar to:
 > # fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       21675    10924168+   5  Extended
/dev/hda2   *       21676       67186    22937544    c  W95 FAT32 (LBA)
/dev/hda3           67187       77545     5220936   83  Linux
/dev/hda5               1         670      337302   82  Linux swap / Solaris
/dev/hda6             670       21675    10586803+  83  Linux

The drive you want to mount _should_ be there.
Now, if you see it, you can mount with the
mount /dev/hdX /media/lost
hdX being your drive and lost your drive point.

---

### Post by Azmodan on 2005-07-26
[QUOTE=bored2k]O.o

Ok, boot the live disc, get in a root terminal and type
```
fdisk -l
```There you should see something similar to:
 

The drive you want to mount _should_ be there.
Now, if you see it, you can mount with the
mount /dev/hdX /media/lost
hdX being your drive and lost your drive point.[/QUOTE]

This works.  Thanks !

Unfortunately, I can't manage to burn something uncorrupted.

I guess I'll lose my data after all.

Any more ideas ?

---

### Post by bored2k on 2005-07-26
[QUOTE=Azmodan]This works.  Thanks !

Unfortunately, I can't manage to burn something uncorrupted.

I guess I'll lose my data after all.

Any more ideas ?[/QUOTE]
 Can't you email the data ?

I still can't believe you're not able to install UBuntu.. And in such case, you could even install Knoppix on your HDD then back up.

---

### Post by Azmodan on 2005-07-26
[QUOTE=bored2k]Can't you email the data ?

I still can't believe you're not able to install UBuntu.. And in such case, you could even install Knoppix on your HDD then back up.[/QUOTE]

Not gigs of it.  This is why I tried to use DVDs instead of just CDs.  I'll try to e-mail the most important files...

---

### Post by Azmodan on 2005-07-27
I did a fresh install and it is already corrupted.  And I didn't even started to configure things yet.  Now, it even refuses to boot.

I guess I have a physical problem with my hard drive.

Any good diagnostic tool ?  Which run from the Ubuntu LiveCD if possible.

Thanks.

---

