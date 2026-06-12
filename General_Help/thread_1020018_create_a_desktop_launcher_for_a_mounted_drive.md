---
title: "create a desktop launcher for a mounted drive"
date: 2008-12-23
forum: General Help
---

### Post by Heeter on 2008-12-23
Hi all,

I mounted some network drives into my fstab. Everything is working fine.

I would like to create desktop launchers for each mounted drive, but I don't know how with my Ubuntu Studio 8.10

Thanks

Heeter

---

### Post by jerome1232 on 2008-12-23
If the shares are mounted under your local file hierarchy then just mount them under /media they should automatically get a desktop icon.

---

### Post by Heeter on 2008-12-23
Where do I put this /media ?


Thanks

Heeter

---

### Post by jerome1232 on 2008-12-23
Well can you post what your fstab look like?

```
cat /etc/fstab
```

---

### Post by Heeter on 2008-12-23
Thanks jerome,

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=78c256fa-5ede-4d7b-b36d-68fc8fffb9d4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=7b857a63-c30f-4793-85df-0acd8385d691 /boot           ext3    relatime        0       2
# /dev/sda4
UUID=2e4f39e6-8675-438d-959d-d9ed7635afed /home           ext3    relatime        0       2
# /dev/sda2
UUID=96550121-e282-4ab9-9349-04b7a8c6c9f2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

//192.168.1.1/Documents /home/user/Documents cifs username=user,password=pass,_netdev,uid=administrator,gid=users,nobrl 0 0
//192.168.1.1/Ftpfiles /home/user/Ftpfiles cifs username=user,password=pass,_netdev,uid=administrator,gid=users,nobrl 0 0
//192.168.1.1/webroot /home/user/Webroot cifs username=user,password=pass,_netdev,uid=administrator,gid=users,nobrl 0 0
//192.168.1.1/Documents/Music /home/user/Music cifs username=user,password=pass,_netdev,uid=administrator,gid=users,nobrl 0 0
//192.168.1.1/Documents/Pictures /home/user/Pictures cifs username=user,password=pass,_netdev,uid=administrator,gid=users,nobrl 0 0

```



Heeter

---

### Post by jerome1232 on 2008-12-23
> **Heeter said:**
> Thanks jerome,

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=78c256fa-5ede-4d7b-b36d-68fc8fffb9d4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=7b857a63-c30f-4793-85df-0acd8385d691 /boot           ext3    relatime        0       2
# /dev/sda4
UUID=2e4f39e6-8675-438d-959d-d9ed7635afed /home           ext3    relatime        0       2
# /dev/sda2
UUID=96550121-e282-4ab9-9349-04b7a8c6c9f2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

[COLOR="Blue"]//192.168.1.1/Documents /media/Documents cifs username=user,password=pass,_netdev,uid=administrator,gid=users,nobrl 0 0
//192.168.1.1/Ftpfiles /media/Ftpfiles cifs username=user,password=pass,_netdev,uid=administrator,gid=users,nobrl 0 0
//192.168.1.1/webroot /media/Webroot cifs username=user,password=pass,_netdev,uid=administrator,gid=users,nobrl 0 0
//192.168.1.1/Documents/Music /media/Music cifs username=user,password=pass,_netdev,uid=administrator,gid=users,nobrl 0 0
//192.168.1.1/Documents/Pictures /media/Pictures cifs username=user,password=pass,_netdev,uid=administrator,gid=users,nobrl 0 0[/COLOR]

```



Heeter

I highlighted in blue the line's I changed, basically instead of mounting them at /home/user/whatever, mount them /media/whatever.

That's the only way I know of to do it.

You may have to create those directories before it'll work.

```
sudo -i
mkdir /media/Documents
mkdir /media/Ftpfiles
 etc...
exit
```

---

### Post by Heeter on 2008-12-23
sorry Jerome, that didn't work.

I do have those folders created already.


Heeter

---

### Post by jerome1232 on 2008-12-23
huh, did you remount the shares?

Well if it didn't work I suppose you could just create symbolic links to them

```
ln -s /path/to/share /home/user/Desktop/sharename
```

For example I wanted to make a link on my desktop called joe, and it pointed at the folder /home/user/joe then that command would be

```
ln -s /home/user/joe /home/user/Desktop/joe
```

---

### Post by Heeter on 2008-12-23
Great Thanks,jerome

That worked.


Heeter

---

