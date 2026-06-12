---
title: "GParted and blkid show different devices"
date: 2009-01-30
forum: General Help
---

### Post by m4lte on 2009-01-30
**SOVLED**

Hi there!

I just noticed that typing blkid lists some devices, which I don't see in GParted. The devices sda6 and sda7 do not appear in GParted (see screenshot).

How does this difference come about?


```

malte@malte-laptop:~$ blkid
/dev/sda1: UUID="CC2A4E602A4E4822" LABEL="SERVICEV003" TYPE="ntfs" 
/dev/sda2: UUID="988E517D8E5154BA" LABEL="windows" TYPE="ntfs" 
/dev/sda3: TYPE="swap" UUID="ce43b32c-43f8-44ca-a174-e3b04d154f60" 
/dev/sda5: UUID="a717d168-bfbe-4798-a5e8-12390d014e64" TYPE="ext3" 
/dev/sda6: UUID="97f78bb1-65d9-465f-84e2-c6222935da83" TYPE="swap" 
/dev/sda7: UUID="E756-D4D6" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

```

---

### Post by caljohnsmith on 2009-01-30
Did you recently change your partitions? If so, just doing "blkid" prints the blkid stored in cache, to get a new listing try:
```
sudo blkid -c /dev/null
```
Is that listing any different?

---

### Post by m4lte on 2009-01-30
Oh yeah, that helped. Now the display is correct.
Thanks!!

---

