---
title: "Network shares in Storage Media (media:/)"
date: 2005-11-27
forum: Desktop Environments
---

### Post by Jens7677 on 2005-11-27
I know that I saw my own smb connection(there are not listed in fstab, just mounted with smb4k) there (thus was able to show them on the desktop as well). But since the integration with hal took place there are vanished (cdrom, usb stick etc are working perfectly). What kind of an issue is this? Needs hal able to detect mounted network shares (is this possible? at least I found a workaround in this forum to let hal run as root so my fixed harddisks where shown again) or should I tell kde somewhere not just use hal but fall back to something else (/mount shows the shares nice) for this kind of mount-points? 

Edit: Just tried kde3.5rc1, and even when disabling hal I can't see them (properly because there a not listed in fstab).

Any ideas?

---

### Post by hyperpsyched on 2006-02-10
I had the same problem... it was weird too because I could see the files using firefox but not Konq...

Tried "adduser hal disk" and while I can now see my drives I can see all my partitions including my NTFS WinXP partition and they all have long inhuman names like "S3DAAA... blah blah".

How can I either:

1. remove 'hal' from 'disk'
2. remove  the NTFS partition from my desktop and media file
3. rename all the partitions to something less Borg-like

 (I wanted a highly configureable OS, if I wanted to be assimilated I would have stuck with XP)

Why is this so freakin' hard to do? Either from the gui or console?

Don't get me wrong, I love the OS but this one little problem is costing me hours...

---

### Post by hyperpsyched on 2006-02-10
I most definately did not post the above message in this thread...

---

