---
title: "can't mount a dvd-rw disk"
date: 2006-09-01
forum: Desktop Environments
---

### Post by songo on 2006-09-01
i've just burned a dvd-rw, and now I can't mount it!

**sudo mount /media/cdrom0** says **mount: block device /dev/hdc is write-protected,***(bla bla bla)*

here's some
[B]# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto     0       0[/B]

what's wrong?

---

### Post by taurus on 2006-09-01
How about

```

sudo mount -t iso9660 /dev/hdc /media/cdrom0
df -h

```

---

### Post by songo on 2006-09-01
> sudo mount -t iso9660 /dev/hdc /media/cdrom0 in this case is the same that ```
sudo mount /media/cdrom0
```
as the -t iso9660 is defined on the /etc/fstab. I wonder if for dvd-rw the <type> field is different?

---

### Post by taurus on 2006-09-01
> **songo said:**
> I wonder if for dvd-rw the <type> field is different?
Nope.  It's the same for both.  By the way, the "mount: block device /dev/hdc is write-protected," message is not an error.  It just tells you that you can only read from it but cannot write to it!  So, try to mount it again and see if it, /media/cdrom0, shows up here...

```
df -h
```

---

### Post by songo on 2006-09-02
[B]ok, from begining

i've just burned a dvd-rw, and now I can't mount it!

sudo mount /media/cdrom0 (or sudo mount -t iso9660 /dev/hdc /media/cdrom0) says:[/B]
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

**df -h gives**
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             4.8G  3.1G  1.5G  69% /
varrun                189M   72K  189M   1% /var/run
varlock               189M     0  189M   0% /var/lock
udev                   10M  108K  9.9M   2% /dev
devshm                189M     0  189M   0% /dev/shm
lrm                   189M   18M  171M  10% /lib/modules/2.6.17-5-386/volatile
/dev/hda5             3.7G  3.5G  6.9M 100% /home

**and dmesg|tail**
[17179599.524000] ibm_acpi: ec object not found
[17179599.584000] pcc_acpi: loading...
[17179604.168000] ppdev: user-space parallel port driver
[17179607.336000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179607.336000] apm: overridden by ACPI.
[17179607.724000] eth0: no IPv6 routers present
[17188053.416000] cdrom: This disc doesn't have any tracks I recognize!
[17188126.972000] attempt to access beyond end of device
[17188126.972000] hdc: rw=0, want=68, limit=4
[17188126.972000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

**here's some**
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

**what's wrong?**

---

