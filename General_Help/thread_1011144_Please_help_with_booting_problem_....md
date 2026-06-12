---
title: "Please help with booting problem ..."
date: 2008-12-14
forum: General Help
---

### Post by olly666 on 2008-12-14
Uninstalled Ubuntu through Vista, now getting Grub error 22...can't boot... I've got Knoppix running now, can anyone tell me what command/s to run to restore original boot menu so that Vista can boot again? Many thanks.

---

### Post by wd5gnr on 2008-12-14
Do you have your Vista install disks? Boot from that.

If so: [http://windowshelp.microsoft.com/windows/en-US/help/2b3724d1-f4ad-5b26-16dc-3e9e66f4be5e1033.mspx](http://windowshelp.microsoft.com/windows/en-US/help/2b3724d1-f4ad-5b26-16dc-3e9e66f4be5e1033.mspx)

Try the Startup Repair option. You could also go to the command prompt and try fixmbr (assuming it is like XP -- not sure about that).

---

### Post by boterbram on 2008-12-14
[http://answers.yahoo.com/question/index?qid=20070909053635AAMN1hx](http://answers.yahoo.com/question/index?qid=20070909053635AAMN1hx)

might help

---

### Post by olly666 on 2008-12-14
Don't have the discs with me as I'm overseas...

There must be a suitable command to run through knoppix, no?

---

### Post by caljohnsmith on 2008-12-14
If Knoppix has Lilo installed, just do:
```
sudo lilo -M  /dev/sda mbr
```
And replace "sda" with the Vista drive if it is different. That will install a Windows MBR to drive sda so you can boot directly into Vista.

---

