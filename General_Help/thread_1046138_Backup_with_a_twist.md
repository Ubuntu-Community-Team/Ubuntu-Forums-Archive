---
title: "Backup with a twist"
date: 2009-01-21
forum: General Help
---

### Post by yeleek on 2009-01-21
Hi,

I want to be able to backup my / and my /home (2 separate partitions) to an external USB.  And in the worst case want to be able to boot from a CD/DVD and restore both partitions.  Asking too much?  Or is there software for Linux out there that I can do this with?  Don't mind if it uses images or files.

Pls advise.

Thanks

---

### Post by hansdown on 2009-01-21
Hi yeleek.

Try Remastersys.

[http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22](http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22)

---

### Post by yeleek on 2009-01-21
That is spot on!  Many thanks :)

---

### Post by Neural oD on 2009-01-21
Is this a once off thing - or do you want to keep the usb synced at all times. Both are easily accomplished and there are many ways to do this. The first is that you could cp -r of your whole home directory and then one of the root partition to the external usb. Another method would be to fire up a live cd and then do a ddrescue on the partition. Look at the man pages for the cp command - one could run a script that updates only the latest changes for example. Also if you want some further apps - on command line type: apt-cache search backup

Regards

---

