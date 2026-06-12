---
title: "Help reformating hard drive."
date: 2005-08-01
forum: Desktop Environments
---

### Post by Der_PK on 2005-08-01
Hi, I am having too many problems with Ubuntu and I would like to go back to windows98 on my old computer. The thing is when I try to reformat through the windows 98 CD, it says there is something wrong with the hard drive. Then it just proceeds to a command prompt. If anyone could help me, I'd really appreciate it!

---

### Post by adwait on 2005-08-01
Hmm thats sad........going back to winblows....

Anyway, what does it say? What's wrong? Its gotta give some explanation right? If not.....start up the ubuntu installer....skip to the partittioning stage, and delete your linux partitions and create fat32 partitions instead, maybe Windows likes that

---

### Post by az on 2005-08-01
Get a windows boot floppy and boot from it.  From the dos command line, type fdisk and erase all your partitions.  Create a new one.

exit fdisk and reboot.  Get used to rebooting again.  Once you reboot into the boot floppy again, format your empty partition.

Start the Windows installer.

---

### Post by Der_PK on 2005-08-01
Oh, this isn't good. My floppy drive died one me a while back. Is it possible through the CD?

---

### Post by Sam on 2005-08-02
Don't format directly (from the Windows setup), but first delete the partition, then recreate it and format after that. Maybe this helps.

---

