---
title: "vmware converter"
date: 2008-02-12
forum: Desktop Environments
---

### Post by Paul Gardil on 2008-02-12
I have a Windows partition on my machine, and I'd like to run VMWare Converter to produce a VM.  However, there's no place to put the VM!

 I did not leave much extra space on the ntfs partition when I shrunk it to make space for Ubuntu, and I can't extend it now, because the ext3 partition comes right after the nfts partition.

I'm thinking of shrinking the ext3 partition to make room for an additional ntfs partition and then using that partition to store the VM, but I have a few questions...

Is it even possible to make a new ntfs partition in GParted?  If so, will Windows automatically recognize it and assign a drive letter to it?  Is this a good plan?

---

### Post by PilotJLR on 2008-02-12
Yes, you could make a new ntfs partition and give it a drive letter...

Do you have any USB hard drives or any cifs shares from other pc's on the network? You could easily use those as well.

---

### Post by PilotJLR on 2008-02-12
If you do make a new partition, go to Disk Management mmc tool in Windows to format and assign a drive letter. The "wizard" should pop up in there when it detects the new space.

I personally would use a USB hard disk or cifs share first, though. If you have that available.

---

