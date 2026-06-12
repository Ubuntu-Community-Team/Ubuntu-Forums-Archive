---
title: "Help!! Can´t save or modify ANY files!"
date: 2005-12-23
forum: Desktop Environments
---

### Post by caesarsgrunt on 2005-12-23
I´ve just installed Ubuntu, and whilst installing I set up a ROOT password and created a normal user account. Now I can´t log on as ROOT with a GUI, and fron the normal account I can´t save or modify any files, or change "advanced" settings! When I click any advanced setting in the System menu, GKsudo asks for my password, and then when I enter it nothing happens!
Please Help!

---

### Post by darth_vector on 2005-12-23
the root account is disabled by default. you can get superuser priviledges by using the sudo command. just use your normal user password.

you shouldnt be able to modify any files that are outside of /home/your_username since they dont belong to you; they belong to root. with sudo you can edit any file - almost - in the filesystem.

---

### Post by caesarsgrunt on 2006-01-12
Sudo doesn´t seem to work for me...
After I´ve entered my password, nothing happens.

I need to be able to access every file on my computer. I tried using chmod, after having booted to a command line as root. I managed to give myself full permissions for accessing "/", but I can´t give myself full access to my other hard drives!

Here´s what I did:
```

chmod -R 777 /media/hda5
chown -R caesar /media/hda5

```
but it didn´t work. Is it the wrong path to hda5?

I managed to log on to the GUI as root by doing the following:
I logged on using the command line, as root.
I entered the following:
```

chmod -R 777 /
chown -R caesar /

```
I edited the file "etc/X11/gdm/gdm.conf", to enable root logon.
I rebooted the computer, and logged on.

However, I still couldn´t change the permissions of hda5 to 777. How should I go about this?


Does anyone know of a more user-freindly version of Linux? I´ve only used Windows before, and I don´t know anything about command-lines etc, but now I need Linux for testing websites which I design.

---

### Post by schilcha on 2006-01-12
What kind of partition is mounted at /dev/hda5? Has it some kind of windows filesystem on it (fat32/ntfs)? If so, chmod and chown will not work on these. ntfs is read only -- no way to modify anything there. fat32 doesn't know about users and permissions as well (to my knowledge). If you want to own files there, you'll need to edit /etc/fstab. Here's what one normally does to do that:
```

sudo gedit /etc/fstab

```
Go to the line containing "/media/hda5" and add "umask=777,uid=YourUID" to the 4th column. Once you added umask, you probably wont need uid, since you enabled full access anyways. Finally remount the partition to activate your changes.
```

sudo umount /media/hda5
sudo mount /media/hda5

```

BTW, you're able to access every file within your computer via sudo. Being the owner of all files and making them world read/write/execuatble is probably not a very good idea -- It seems like making your linux-box more windowish by introducing ill-defined user-permissions -- a situation that made windows so vulnerable to all kinds of malware.

---

