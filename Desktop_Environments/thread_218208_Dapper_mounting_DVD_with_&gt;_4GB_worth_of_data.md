---
title: "Dapper mounting DVD with &gt; 4GB worth of data"
date: 2006-07-18
forum: Desktop Environments
---

### Post by roland67 on 2006-07-18
Hi,
Wonder if anyone can help. 

I've installed Dapper Drake 6.06 on a DELL Inspiron 6000 laptop, completely over-writing (i.e. erasing and installing ontop) the previously installed version - 5.10.

On 5.10 this laptop could quite happily read DVD's with > 4GB's worth of data, DVD's burnt on Windows or on Linux.

Now, with Dapper Drake it has wierd problems.

If I insert the DVD with > 4GB's worth of data, it does not automount.
If I type (as root), "mount /media/cdrom0" I get: 


"
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ro-laptop1:~# dmesg | tail
"

If I then look at dmesg | tail, I see: 

"[17179865.408000] ISO 9660 Extensions: Microsoft Joliet Level 1
[17179865.420000] ISOFS: changing to secondary root
[17187173.772000] attempt to access beyond end of device
[17187173.772000] sr0: rw=0, want=68, limit=4
[17187173.772000] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[17187196.536000] attempt to access beyond end of device
[17187196.536000] sr0: rw=0, want=68, limit=4
[17187196.536000] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
"

This particular DVD in question works fine on Windows, I've tried it.

Any suggestions anyone?
Thanks, Roland

---

### Post by taurus on 2006-07-18
Try this then (from a terminal)!

```

sudo mount -t iso9660 /dev/scd0 /media/cdrom0

```

---

### Post by roland67 on 2006-07-18
Same message: 
"
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
"

dmesg | tail: 

[17179865.408000] ISO 9660 Extensions: Microsoft Joliet Level 1
[17179865.420000] ISOFS: changing to secondary root
[17187173.772000] attempt to access beyond end of device
[17187173.772000] sr0: rw=0, want=68, limit=4
[17187173.772000] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[17187196.536000] attempt to access beyond end of device
[17187196.536000] sr0: rw=0, want=68, limit=4
[17187196.536000] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[17187809.984000] attempt to access beyond end of device
[17187809.984000] sr0: rw=0, want=68, limit=4
[17187809.984000] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

dmesg | tail seems to contain the same information, may not have been updated.

---

