---
title: "Samba server help"
date: 2009-04-29
forum: General Help
---

### Post by theRick on 2009-04-29
I just reinstalled my home server with 9.04

I previously had this server running as a samba server with 8.10

I am trying to the same two external hard drives as I was using previously but I'm having 2 problems.

1. The shares show up in wondows, but the folders say they are only 2gb even though one drive is 250gb and the other is 500gb.

2. The files that are already on the drive don't show up at the ubuntu command line or in the samba shares.

How do I get those files to reappear?

The drives are formatted NTFS and samba is setup according to the [9.04 guide]("https://help.ubuntu.com/9.04/serverguide/C/samba-fileserver.html")

Help!

My fstab file looks like this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=45bdff1a-06ce-499b-873a-5ff390e17d14 /               ext3    relatime,erro$
# /dev/sda6
UUID=3857cbe2-2e20-44db-b392-d6e27ea8f5ed none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 /media/filestorage ntfs defaults 0 0
/dev/sdc1 /media/mediastorage ntfs defaults 0 0
```

---

