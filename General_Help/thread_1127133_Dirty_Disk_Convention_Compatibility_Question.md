---
title: "Dirty Disk Convention Compatibility Question"
date: 2009-04-16
forum: General Help
---

### Post by DrHow on 2009-04-16
I am dual booted with Vista and Ubuntu.  I have an NTFS partition that both OSs can share.  If there is a power failure or other crash that leaves the disk dirty, is it important to first reboot the same OS that was active when the crash occurred?  I have been wondering about this for some time, and my attempts at searching for an answer have not produced much.  What I am worrying about is that Vista might have left the disk dirty, that Ubuntu is booted first (by default) after the crash, and that Ubuntu is not aware of the dirty condition because it uses a different convention for indicating a dirty disk.  

If Ubuntu is aware of the dirty condition, does it know what to do about it?  

If Ubuntu leaves the disk dirty, will Windows realize it?

---

### Post by StuartN on 2009-04-16
A crash in Ubuntu should have no effect at all on Windows, so it doesn't matter if you boot into Windows before booting Ubuntu again.

If there is a crash in Windows (or if an external NTFS drive is removed without a safe ejection) then the NTFS partition is marked as having an unclean shutdown. The best way of resetting the mark is by booting Windows and shutting down cleanly. If you do boot Ubuntu then you may not be able to mount the NTFS partition - of course there is an option to force mounting and a tool to fix NTFS, but data loss is less likely using Windows to recover a Windows NTFS error.

---

### Post by DrHow on 2009-04-16
> **StuartN said:**
> A crash in Ubuntu should have no effect at all on Windows, so it doesn't matter if you boot into Windows before booting Ubuntu again.


I am not sure I understand this.  As I said, I intend to use my Ubuntu system to access an NTFS partition which Windows can also access.  If the power fails when Ubuntu has a file open for output on that partition, then it seems to me that the partition is dirty, that this **does** affect Windows, and that Windows had better know about it.  What am I missing?

As can be inferred from the title of this thread, one of the main points of my question was whether or not Windows and Ubuntu use the same convention for marking a disk dirty.  I think I can infer "yes" from Stuart's comments, but I would really like to know this more explicitly.

> 
If there is a crash in Windows (or if an external NTFS drive is removed without a safe ejection) then the NTFS partition is marked as having an unclean shutdown. The best way of resetting the mark is by booting Windows and shutting down cleanly. If you do boot Ubuntu then you may not be able to mount the NTFS partition - of course there is an option to force mounting and a tool to fix NTFS, but data loss is less likely using Windows to recover a Windows NTFS error.

I think that you are saying that, if, after a power failure when Windows had a file open on the partition and the next boot is to Ubuntu, then Ubuntu will realize that there is a problem but it will not take any action to attempt to correct the problem without authorization.  Since my Grub setup has Ubuntu as the default system to load on boot, I believe that I can expect this situation to eventually arise in practice.

---

