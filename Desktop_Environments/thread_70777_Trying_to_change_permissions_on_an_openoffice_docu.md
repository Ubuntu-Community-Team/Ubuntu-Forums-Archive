---
title: "Trying to change permissions on an openoffice document"
date: 2005-10-01
forum: Desktop Environments
---

### Post by The Waco Kidd on 2005-10-01
I've just installed Kubuntu 5.10 on a dual boot with Windows XP. I've got a shared FAT32 partition where I keep my documents.

The problem is - Ubuntu seems to have assigned everything on the shared partition to root. Everything opens as 'read-only' and I can't work out how to change permissions so I can actually do some usefull work. I've tried logging in as root (not allowed) and tried using kuser to add myself to the 'root' group (doesn't seem to make any difference). 

Please help!

---

### Post by adwait on 2005-10-01
Open up the /etc/fstab file using
```

sudo gedit /etc/fstab

```

Now find the partition that you want, and in the options the following
```

uid=1000,gid=1000

```
This is considering you are the ifrst user created onthe system.....if not, enter the number it shows when you wnter this command:
```

echo $UID

```

---

### Post by GTvulse on 2005-10-01
You need to assign ownership of the files in the partition to your accont at mounting time. I have a dual boot setup such as yours and this is what I have in my /etc/fstab file:
```
/dev/hda9    /media/hda9    vfat    utf8,user,uid=1000,gid=1000    0   0
```
Where uid=1000 and gid=1000 are the numeric system IDs for the user and default group the user belongs to. If you are using the account created when your installed Ubuntu the IDs in your system they will be the same. With this setup I can read and write files to the FAT32 partiton without a problem.

(PS, if you find the directory name a bit strange, it is the default setup in Breezy :-))

---

### Post by The Waco Kidd on 2005-10-01
Thankyou both! Worked a treat :D

---

