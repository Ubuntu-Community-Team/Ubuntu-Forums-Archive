---
title: "mounting with read AND write privileges"
date: 2005-11-11
forum: Desktop Environments
---

### Post by jeffjanzen on 2005-11-11
in my fstab, i have a fat32 partition listed, with the following options:
```
<file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hdb5       /fat32          vfat    defaults        0       0
```
when i run a specific application as 'root', i have full read and write priviliges to the partition, but most of the time i'm not running my applications as root, and the partition is read-only.  i cannot write data to the fat32 partition as a normal user, only as 'root'.
i've tried changing the permissions for the folder where the partition is mounted in several different ways:
in the folder properties dialog from nautilus:  it's strange, i check the boxes for allowing 'write' privileges to 'group' and 'other' users, but the box changes right back to being unchecked, in a manner of milliseconds, right before my eyes :confused: .  when i try to change the 'file owner' or the 'file group', i get an error message: "Sorry, couldn't change the owner of 'fat32'".
i've tried 'chmod' and 'chown' commands at the root terminal (even tried booting in 'recovery mode'), but bash returns "Operation not permitted".
i've also tried changing the mount point to /home/jeffjanzen/fat32, thinking that i would automatically have read privileges if it was in my home directory, but that didn't work either.
what's the deal?  is this some kind of security measure built into debian or ubuntu to protect my fat32 partition?  i just want to be able to write to my fat32 hard drive as a normal user.

---

### Post by audax321 on 2005-11-11
Change defaults to:  umask=000

:)

---

### Post by aysiu on 2005-11-11
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by audax321 on 2005-11-11
One thing about the guide though. It says to put the options as:

iocharset=utf8,umask=000

but, I remember getting errors saying that utf8 was not a compatible charset set for FAT32 when booting and mounting (might not see this with the splash in the way). So, I just got rid of it and kept the umask=000 which is the way I've been mounting FAT32 for years.

---

### Post by aysiu on 2005-11-11
Yeah, I've been getting that warning at boot up for months, and I haven't had any problems, either. If you read the warning carefully, it just says utf8 isn't recommended because it's case sensitive.

---

### Post by abenton on 2005-11-12
I've got a similar problem. I have a regular hard drive where ubuntu is loaded and a secondary SATA drive that is formatted as a FAT drive. Prior to version 5.10, I had to manually mount the SATA drive but I could read and write to it as a regular user. Since I upgraded to 5.10 though, an icon appears on the desktop and I can view/use programs & files on the drive but I can't save or delete from the hard drive. I've messed around with fstab a good bit. umask=000 improves things some. But I'd like to change the ownership of everything on this drive from root to me. sudo chown doesn't work. 

I know there were some issues with SATA drives on the last version and there are probably still plenty of issues with these drives. Any thoughts or suggestions to try here would be appreciated!

---

### Post by jeffjanzen on 2005-11-12
[QUOTE=audax321]Change defaults to:  umask=000

:)[/QUOTE]
WORKS GREAT NOW!  THANKS!

---

### Post by Irony on 2005-11-12
To get rid of the warnings about compatible charsets use;

[PHP]/dev/hda1       /mnt/fat  vfat    defaults,umask=000  0       0[/PHP]

---

### Post by slux on 2005-11-12
umask=000 is a bit drastic, though. A more restricted approach would be to give uid=<your uid> which will result in all the files being owned by the user. If you've got many users accessing your system this might be either a good or bad thing but it feels a bit un-UNIX to just grant total access to everyone.

---

### Post by audax321 on 2005-11-12
[QUOTE=slux]umask=000 is a bit drastic, though. A more restricted approach would be to give uid=<your uid> which will result in all the files being owned by the user. If you've got many users accessing your system this might be either a good or bad thing but it feels a bit un-UNIX to just grant total access to everyone.[/QUOTE]

I see what your saying, but what's more un-UNIX than using FAT32 ;)  Anyway, does setting the uid like that have any affect on the files under Windows?

---

### Post by slux on 2005-11-12
[QUOTE=audax321]I see what your saying, but what's more un-UNIX than using FAT32 ;)  Anyway, does setting the uid like that have any affect on the files under Windows?[/QUOTE]

Yeah, I know. It's completely irrational and doesn't make much of a difference ;)

Nope, FAT32 doesn't have no concept of file ownership and it's only affects the mounting under GNU/Linux.

---

