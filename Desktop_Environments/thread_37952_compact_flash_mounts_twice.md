---
title: "compact flash mounts twice"
date: 2005-05-29
forum: Desktop Environments
---

### Post by veritas366 on 2005-05-29
I thought I'd try out my compact flash reader...it's a lexar jumpstart.  Weird thing is, it mounts twice as 65M Removable Media and 65M Removable Media (2).  I don't unmount and remount or anything.  

> root@ubuntu:~ # cat /proc/scsi/scsi
Attached devices:
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: Lexar    Model: Jumpshot USB CF  Rev: 0001
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi1 Channel: 00 Id: 00 Lun: 01
  Vendor: Lexar    Model: Jumpshot USB CF  Rev: 0001
  Type:   Direct-Access                    ANSI SCSI revision: 02 

This is the first time I've tried this.  The "would you like to import photos" dialogue starts up twice, but does not work.  However dragging and dropping works perfectly fine, so it can read files.  When I try the import photos it says "no camera found".  I guess I don't really need this automated feature, though now that I try it again that dialogue doesn't even come up.

However, the double mounting concerns me.  Any ideas?

---

### Post by veritas366 on 2005-05-30
anyone?  anyone?  Bueller?  Bueller?

---

