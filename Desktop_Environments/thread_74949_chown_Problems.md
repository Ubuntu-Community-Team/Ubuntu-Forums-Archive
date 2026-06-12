---
title: "chown Problems"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Jeff Hunter on 2005-10-13
Okay, I have a slight problem.  I am fairly new to Linux, and have just recently figured out how to mount my Windows file system to a folder.  However, I can only read and copy the files from my user, only root has permission to write and so forth.  I tried chown foldername -R, but it gives me a list of every file in the directory followed by "Operation not permitted".  Gives me the same results with both root and with the sudo command.

I have mounted it to /home/jeffhunter/C: and typed (as root) chown jeffhunter /home/jeffhunter/C: -R, and it spits out the above error message.

The windows file system is FAT 32 and has no problems with read/write under root, just lists as root owner and will not let me change the owner or the permissions to anything but 755.

If anyone has any insight (or reallizes that I am beeing a bafoon and knows what I am doing wrong), please help.  It really is a pain to have to use the terminal when I am still getting used to it to do anything of importance with that file system.

Jeff Hunter

"I am NOT a Nerd!  I am a GEEK!  Get it right!"

---

### Post by Pablo_Escobar on 2005-10-13
Please, paste Your /etc/fstab file here, because with right masks You should be able to automount at boot, and standard user should have FAT32 write access.

---

### Post by Jeff Hunter on 2005-10-13
Will do, but I still would like to figure out what I am doing wrong with chown...I am rather stubborn that way, after all, how else will I learn?

Well, there is the continue to bang my head against a wall approach, but I've been doing that so long I'm running out of asprin.

---

### Post by Jeff Hunter on 2005-10-13
Okay, here is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               reiserfs notail          0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

Also, dev/hda1 is my C:\ partition and dev/hda5 is my D:\.  Both are on IDE 0, with dev/hdb1 being located on IDE 1

I have been mounting hda1 to /home/jeffhunter/C: and hda5 to /home/jeffhunter/D:

No matter what I seem to do, however, it is always mounting it with root as owner and permissions set to 755.  It has not yet let me change this with either chown or chmod, saying that the Operation is not permitted, even when logged on as root.

I thought root was allowed to do just about everything?  Please help

---

### Post by Pablo_Escobar on 2005-10-13
Don't know about chown but You can easily make this partition avalible:
Paste the following in Your fstab at the new line:
/dev/hda1       /home/jeffhunter/C  vfat    iocharset=utf8,umask=000   0       0
/dev/hda5       /home/jeffhunter/D  vfat    iocharset=utf8,umask=000   0       0

then, if You created these C , D folders in jeffhunter type "sudo mount -a".
And voila.

Maybe a long shot but You wanted to mount at "/home/jeffhunter/C:" - loose ":" at the end, maybe it's causing problems ???

---

### Post by Jeff Hunter on 2005-10-13
Well, I tossed the :, but it is still doing the same thing.  Have not tried the fstab edit you recommended yet, but will try that tomorrow.  Right now, I really should be off to bed.

Anywho, thanks for the help!  Anyone else have any ideas about my chown and chmod problems would be appriciated!

Gnight!

---

### Post by Pablo_Escobar on 2005-10-13
Little man work - ** chown -R jeffhunter /home/jeffhunter/C ** :D

---

### Post by Wolki on 2005-10-13
[QUOTE=Jeff Hunter]If anyone has any insight (or reallizes that I am beeing a bafoon and knows what I am doing wrong), please help.  It really is a pain to have to use the terminal when I am still getting used to it to do anything of importance with that file system.[/QUOTE]

Not sure, but it could be because FAT32 doesn't support file permissions, so chown/chmod can't set them. Setting them in the /etc/fstab should work without problems.

---

### Post by gpayo on 2005-10-13
From the mount manual:
"Mount options for FAT
...

quiet  Turn on the quiet flag.  [B]Attempts to chown or
       chmod files do not return errors, although they
       fail[/B]. Use with caution!
"

I think there is not posible to chown a FAT filesystem.

You can mount you filesystem using the command:

mount -t vfat -o uid=jeffhunter /dev/hda1 /home/jeffhunter/C

This way will mount the disk and all the files will own to the "jeffhunter" user.

Or you can add the follow line in your /etc/fstab :
/dev/hda1    /home/jeffhunter/C   vfat   defaults,user,noauto   0 0

I hope this help...

---

### Post by Jeff Hunter on 2005-10-13
[QUOTE=gpayo]From the mount manual:
"Mount options for FAT
...

quiet  Turn on the quiet flag.  [B]Attempts to chown or
       chmod files do not return errors, although they
       fail[/B]. Use with caution!
"

I think there is not posible to chown a FAT filesystem.

You can mount you filesystem using the command:

mount -t vfat -o uid=jeffhunter /dev/hda1 /home/jeffhunter/C

This way will mount the disk and all the files will own to the "jeffhunter" user.

Or you can add the follow line in your /etc/fstab :
/dev/hda1    /home/jeffhunter/C   vfat   defaults,user,noauto   0 0

I hope this help...[/QUOTE]

Okay, the mount command did work.  Thank you!  I highly appriciate it.  Too bad that the FAT 32 is such a pain to work with from Linux since I can't really change it to anything that works well without destroying Windows (some would see this as a good thing)

Now, as for the [COLOR="Blue"]defaults,user,noauto 0 0[/COLOR], I'm curious...what do those do, indivitually?

---

### Post by gpayo on 2005-10-14
[QUOTE=Jeff Hunter]Okay, the mount command did work.  Thank you!  I highly appriciate it.  Too bad that the FAT 32 is such a pain to work with from Linux since I can't really change it to anything that works well without destroying Windows (some would see this as a good thing)[/QUOTE]
[COLOR="DarkRed"]You are welcome![/COLOR]

[QUOTE=Jeff Hunter]Now, as for the [COLOR="Blue"]defaults,user,noauto 0 0[/COLOR], I'm curious...what do those do, indivitually?[/QUOTE]

Really is quite simple:
The /etc/fstab file has six columns:
1. The device to mount
2. The target directory you want to mount the device
3. The filesystem that is using the device (the word "auto" means the mount command will try to guess the fs)
4. Is a list of options which mount should use when mounting the filesystem. The word "defaults" is like a bunch of options which are:
  4.1 rw: The device mounts as Read/Write
  4.2 suid: Allows to use the set-uid and set-gid bits
  4.3 dev: The device can hold files that describes devices
  4.4 exec: Permit executions of binaries
  4.5 auto: Can be mounted using the mount -a command
  4.6 nouser: Forbid normal user to mount the device
  4.7 async: The I/O to that fs should be asynchronously.

You can find additional options for specific filesystem using "man mount"

5. Is used by dump (a backup utility) to decide if a filesystem should be backed up. If zero then dump will ignore that filesystem.

6. Is used by fsck (the filesystem check utility) to determine the order in which filesystems should be checked.

If you want to go deeper a google search will retrive good info.

Cheers!

---

