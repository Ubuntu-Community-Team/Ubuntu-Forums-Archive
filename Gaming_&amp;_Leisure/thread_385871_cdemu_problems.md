---
title: "cdemu problems"
date: 2007-03-16
forum: Gaming &amp; Leisure
---

### Post by activatekillswitch on 2007-03-16
Help! I'm trying to mount clone cd images (.ccd) using cdemu.
cdemu is working perfectly, mounts the image, ```
cdemu -s
``` tells me that the disk is mounted, but 
```
sudo mount -t iso9660 -o ro /dev/cdemu0 /media/cdemu0 
```
always gives me the error
```

       mount: wrong fs type, bad option, bad superblock on /dev/cdemu0,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I have searched forums till I'm sick of the sight of them but haven't found a solution.
Any help would be most welcome.

P.S. I'm running a P4 3.2Ghz  with 1gb ram, Dapper drake installed but I think updated to edgy, Newest kernel etc.

---

