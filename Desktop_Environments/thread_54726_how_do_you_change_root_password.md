---
title: "how do you change root password"
date: 2005-08-05
forum: Desktop Environments
---

### Post by royg1234 on 2005-08-05
how do you change the root password?  (I didn't lose it, I just have it set to "a" right now, which no bueno).

I changed it in gnome "Users and Groups", but when I do a do a sudo, it takes only my old password ("a"). I want the sudo, su, and gksudo password to change also.

---

### Post by woedend on 2005-08-05
your sudo password, as well as every other password you'll ever use with Ubuntu, is the one that is set to your username.  Which is why changing the root password doesn't change the sudo'ing.  However, su is generally not recommended using to me at least, unless you have a ton of commands to run and don't want to use sudo each time.  su, now, will need the root password.  but sudo does not.  hope this helps.

---

### Post by erik-the-red on 2005-08-05
[QUOTE=woedend]your sudo password, as well as every other password you'll ever use with Ubuntu, is the one that is set to your username.  Which is why changing the root password doesn't change the sudo'ing.  However, su is generally not recommended using to me at least, unless you have a ton of commands to run and don't want to use sudo each time.  su, now, will need the root password.  but sudo does not.  hope this helps.[/QUOTE]
 I even forgot how I did it.

I think I did "sudo passwd root".

---

### Post by woedend on 2005-08-06
system -> administration -> users and groups 
click box at bottom that says 'show all'
click root
click properties

---

### Post by royg1234 on 2005-08-06
thanks.  Now another, unrelated thing:

I want to mount a big FAT32 drive on boot-up with read/write for me.  For everyone else, I want to give only read-only only for certain folders (music).  How do I modify the /etc/fstab line?  This is what I currently have:

```
/dev/sda5       /mnt/files      vfat          iocharset=utf8,umask=000    0       0
```

---

### Post by whoiam55 on 2005-08-06
Hello royg1234

I don't think you can assign permission on certain folders in FAT FS. You would need an ext3,reiserfs or a standard linux fs

---

### Post by whoiam55 on 2005-08-06
[QUOTE=whoiam55]Hello royg1234

I don't think you can assign permission on certain folders in FAT FS. You would need an ext3,reiserfs or a standard linux fs[/QUOTE]

Erm....... wait I think you can

use the "uid" option, combined with "gid" and "umask" something like this

umask=022,uid=<your user id>,gid=<gid of users group>

---

### Post by woedend on 2005-08-06
[QUOTE=whoiam55]Erm....... wait I think you can

use the "uid" option, combined with "gid" and "umask" something like this

umask=022,uid=<your user id>,gid=<gid of users group>[/QUOTE]
 using user ID and group Id is not necessary, only one or the other need be used. I'll show you mine.
/dev/hda3 <tab> /home/woe/c <tab> vfat <tab> gid=1000,umask=002,noexec,nosuid 0 0


now, in your case, i'd use uid instead of gid.  This will make you the Owner of the drive so that you can change individual properties of the folders, such as making them read only one by one.  Find your user ID by going to users and groups.  From my example above, you'd replace gid with uid and the appropriate number.  Then, reboot and see where your files mounted, and right click each folder and select properties.  The set the permissions accordingly.

---

