---
title: "Buffer I/O error on sda1"
date: 2006-11-20
forum: Desktop Environments
---

### Post by jewishj on 2006-11-20
I am using Ubuntu Dapper which is being run off of a SATA RAID 0 (2x WD Raptors using DMRaid).

Recently, an error message started appearing during boot.  It appears right after the splash screen finishes listing out all of the modules it is starting and before X launches (only for a second).  I noticed it originally, when I was having some issues with a version mismatch between the kernel and my NVIDIA drivers ([http://ubuntuforums.org/showthread.php?t=302739)](http://ubuntuforums.org/showthread.php?t=302739)).  The error says:

```

[17179603.016000] Buffer I/O error on device sda1, logical block 36304864
[17179603.016000] Buffer I/O error on device sda1, logical block 36304864

```

the RAID is the only SATA device so I assume sda1 refers to one of the two drives in the array.  This error, however, doesn't seem to affect anything though.  I haven't noticed any performance problems, reliability issues, file corruption, etc.

My question is, is this error indicative of something major like a hdd going bad, partially corrupted filesystem, etc. or just something irrelevant like maybe it has problems reading the hdd by itself because it is part of a RAID?

Thanks for any insight on this

---

### Post by dcstar on 2006-11-21
> **jewishj said:**
> I am using Ubuntu Dapper which is being run off of a SATA RAID 0 (2x WD Raptors using DMRaid).

Recently, an error message started appearing during boot.  It appears right after the splash screen finishes listing out all of the modules it is starting and before X launches (only for a second).  I noticed it originally, when I was having some issues with a version mismatch between the kernel and my NVIDIA drivers ([http://ubuntuforums.org/showthread.php?t=302739)](http://ubuntuforums.org/showthread.php?t=302739)).  The error says:

```

[17179603.016000] Buffer I/O error on device sda1, logical block 36304864
[17179603.016000] Buffer I/O error on device sda1, logical block 36304864

```

the RAID is the only SATA device so I assume sda1 refers to one of the two drives in the array.  This error, however, doesn't seem to affect anything though.  I haven't noticed any performance problems, reliability issues, file corruption, etc.

My question is, is this error indicative of something major like a hdd going bad, partially corrupted filesystem, etc. or just something irrelevant like maybe it has problems reading the hdd by itself because it is part of a RAID?

All of the above.........:( 

If possible, you should probably do a low-level bad block scan of the disk, there could well be a bad block at that location that the RAID system is masking.

---

### Post by jewishj on 2006-11-21
> **dcstar said:**
> All of the above.........:( 

If possible, you should probably do a low-level bad block scan of the disk, there could well be a bad block at that location that the RAID system is masking.


Do you know of a good diagnostic tool like that which will run either from linux or independent of an OS because the only one's that WD offers for the drives are Windows/DOS.

Thanks

---

### Post by warlock_handler on 2007-03-09
Ya mee too.. i am having the same error... help me toooo

---

