---
title: "convert fat32 to ntfs on dual boot"
date: 2005-12-21
forum: Desktop Environments
---

### Post by missmoondog on 2005-12-21
hello,
searched but didn't find quite what i needed. a friend asked me if it was safe to convert his windows xp partition from fat32 to ntfs without doing any harm? i don't see why there should be, but........................................    

thanks

---

### Post by audax321 on 2005-12-21
There is nothing wrong with converting the partition from FAT32 to NTFS, but:

1. NTFS will be mounted as read-only under Linux and can't be written to without risking corruption.

2. All the data on the formatted partition will be lost.

3. After reinstalling Windows, GRUB will have to be reinstalled so the computer can boot into both Windows and Linux again.

---

### Post by aamukahvi on 2005-12-21
There's no need to format the drive :)

just fire up cmd.exe and:
```
convert c: /fs:ntfs
```
(Substitute c: for whichever drive it is you want to convert) If you convert drive C:, you must reboot. It will handle the conversion during boot-up.

So only #1 of the above post is what you need to consider. Just remember that there's no turning back, NTFS --> FAT32 is a no-no.

---

### Post by handy on 2005-12-21
PartitionMagic running on windoze can convert from ntfs to fat32 I believe.

Cheers,

handy

---

### Post by aamukahvi on 2005-12-21
[QUOTE=handy]PartitionMagic running on windoze can convert from ntfs to fat32 I believe.

Cheers,

handy[/QUOTE]
You're right. ;)  But in my experience, that's not too reliable. :o

---

### Post by audax321 on 2005-12-22
Interesting.. I never knew you could convert without formatting... guess you learn something new everyday ;)

---

### Post by missmoondog on 2005-12-22
i knew you could convert without formatting and there is a simple tool right in windows for doing that, just wondered if it would screw anything, especially in ubuntu, up.

thanks

---

### Post by frodon on 2005-12-22
I confirm that converting fat32 to ntfs **could **(it's not 100% reliable) work without data lost.

---

