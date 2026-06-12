---
title: "Can't open an .odt document through the LAN"
date: 2006-07-03
forum: Desktop Environments
---

### Post by calande on 2006-07-03
I have a file server in the office that runs SAMBA. I am on an Ubuntu work station and I tried to open an .odt (OpenOffice.org) file on the file server here, but OpenOffice.org doesn't see the local network, just the file on my computer. Also, if I open Nautilus, browser to the samba share where my file is located and try dragging/dropping the .odt file into OpenOffice.org, I get an error message.

In the same remote directory, trying opening an image file or text file works just fine, just as if it were located on my computer. How could I solve this problem?
Thanks,

---

### Post by calande on 2006-07-03
Any idea? It seems so incredible!

---

### Post by queenorych on 2006-07-03
Nautilous uses gnome-vfs to read samba shares.  It actually doesn't mount anything (generally).  Openoffice to my knowledge doesn't use gnome-vfs or any samba share reading libraries. 

If you want to read samba shared files without copying them first, see smbmount.  Smbmount will add the share to your filesystem as just a regular directory, which openoffice knows all about.

---

### Post by calande on 2006-07-04
[QUOTE=queenorych]Nautilous uses gnome-vfs to read samba shares.  It actually doesn't mount anything (generally).  Openoffice to my knowledge doesn't use gnome-vfs or any samba share reading libraries. 

If you want to read samba shared files without copying them first, see smbmount.  Smbmount will add the share to your filesystem as just a regular directory, which openoffice knows all about.[/QUOTE]

Thank you, with much struggle, I managed to install smbfs, but I get an error message while mounting the lan:

```
root@ubuntu:/media# mount -t smbfs //servidor /media/servidor
Usage: mount.smbfs service mountpoint [-n] [-o options,...]
Version 3.0.22

Options:
      username=<arg>                  SMB username
      password=<arg>                  SMB password
      credentials=<filename>          file with username/password
      krb                             use kerberos (active directory)
      netbiosname=<arg>               source NetBIOS name
      uid=<arg>                       mount uid or username
      gid=<arg>                       mount gid or groupname
      port=<arg>                      remote SMB port number
      fmask=<arg>                     file umask
      dmask=<arg>                     directory umask
      debug=<arg>                     debug level
      ip=<arg>                        destination host or IP address
      workgroup=<arg>                 workgroup on destination
      sockopt=<arg>                   TCP socket options
      scope=<arg>                     NetBIOS scope
      iocharset=<arg>                 Linux charset (iso8859-1, utf8)
      codepage=<arg>                  server codepage (cp850)
      unicode                         use unicode when communicating with server
      lfs                             large file system support
      ttl=<arg>                       dircache time to live
      guest                           don't prompt for a password
      ro                              mount read-only
      rw                              mount read-write

This command is designed to be run from within /bin/mount by giving
the option '-t smbfs'. For example:
  mount -t smbfs -o username=tridge,password=foobar //fjall/test /data/test
root@ubuntu:/media#
```

But /bin/mount is a file, not a directory, so how can you run within /bin/mount ? This is complicated, it should work out of the box. Is there an Ubuntu wishlist somewhere? :-|
Thanks,

---

### Post by calande on 2006-07-04
Ok, I found out, it's working fine now. But I want to add this to the Ubuntu wishlist.

---

### Post by Matthew Bartram on 2006-07-04
I think the easiest is to go to nautilus, go to the directory you want to mount, right click on it, and select "connect to this server"

---

### Post by calande on 2006-07-04
It worked so-so. I can't mount shares that have names with spaces. I tried putting single quotes and double quotes, but it didn't work:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /mnt/windows    ntfs    ro,user         0       0
/dev/sda2       /mnt/backup     vfat    defaults        0       0
/dev/sda5       /mnt/centos     ext3    defaults        0       2
/dev/sdb1       /mnt/docs       vfat    defaults        0       0
/dev/sda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
none            /mnt/ramfs      ramfs   rw,user,auto    0       0
"//servidor/Documentos Internos"        /mnt/interno    smbfs   rw,user,auto    0       0

```

---

### Post by calande on 2006-07-05
How can I execute a command during boot up automatically? Is there a file where I can put a command and it'll execute it each time I start my computer?

---

### Post by Virtual DarKness on 2008-05-02
FYI, I've found a easy/gui based solution for kubuntu users: smb4k lets you see and mount on the fly samba shares and it also see other resources like printers.

bye

---

