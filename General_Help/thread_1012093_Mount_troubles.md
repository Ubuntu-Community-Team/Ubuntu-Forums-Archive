---
title: "Mount troubles"
date: 2008-12-15
forum: General Help
---

### Post by epswing on 2008-12-15
Ubuntu 8.10, Intel Core 2 1.86ghz, geforce 8800 gts, 4gb memory, WD caviar.

I have a nas (DNS-323).  I can browse it from File Browser by typing smb://mynas/afolder as a location. I want to mount afolder at /media/afolder, but the mount command says "wrong fs type, bad option, bad superblock on //mynas/afolder".

I'm coming from Windows XP.  I want to "map a networked drive".  Am I on the right track here?

Command I'm using:
```
sudo mount //mynas/afolder /media/afolder
```

Error I'm getting:
```
mount: wrong fs type, bad option, bad superblock on //mynas/afolder,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I've also tried (all resulting in the same error):
```
sudo mount -t smbfs //mynas/afolder /media/afolder
```
```
sudo mount -t cifs //mynas/afolder /media/afolder
```

Tried using all above commands with the actual ip address.

Tried to invoke mount.cifs directly with
```
sudo mount.cifs //mynas/afolder /media/afolder
```
and got
```
sudo: mount.cifs: command not found
```

There's no username or password on the NAS.  In windows, Start -> Run -> \\mynas\afolder brought up files directly.

smbfs is listed in /proc/filesystems
```

me@mymachine:~$ cat /proc/filesystems | grep smb
nodev	smbfs

```

Synaptic Package Manager says smbclient and sambda-common are installed.

Help!

---

### Post by epswing on 2008-12-16
Anyone?  It can't be this hard to mount a drive...

---

### Post by jcsteele on 2008-12-16
a google for "mounting smbfs" turned up quite a lot of results, specifically: 

[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

