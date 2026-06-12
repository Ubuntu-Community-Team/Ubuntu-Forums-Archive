---
title: "CD writing and Verification using command line"
date: 2009-03-28
forum: General Help
---

### Post by openfreak on 2009-03-28
Hi guys
I need to learn about how to burn and verify a cd/dvd in comand line. some of the suggestion I have come accross are making an iso from the cd/dvd and comparing its md5sum with the original iso used in burning the cd. But it is little more time consuming..........burn the dvd->make iso from it and.........then calculate its md5sum.
Also when burning from commandline is it necessary to make an iso prior to burning the data, can't it be burnt directly to the disk.

---

### Post by SuperSonic4 on 2009-03-28
There is some data there: [https://help.ubuntu.com/community/CdDvd/Burning#Command%20Line%20(Terminal](https://help.ubuntu.com/community/CdDvd/Burning#Command%20Line%20(Terminal))

---

### Post by openfreak on 2009-03-29
> **SuperSonic4 said:**
> There is some data there: [https://help.ubuntu.com/community/CdDvd/Burning#Command%20Line%20(Terminal](https://help.ubuntu.com/community/CdDvd/Burning#Command%20Line%20(Terminal))


SuperSonic4

I seen that but what about media verification after it is burnt,I also want to learn that

---

### Post by azc on 2009-03-29
> 
I seen that but what about media verification after it is burnt,I also want to learn that


To verify the CD, I do the following:

-------------------------------------------------------------------------------

1. Calculate the CD MD5SUM, and compare to the ISO MD5SUM.

```

$ dd if=/dev/scd0 | head -c `stat --format=%s filename.iso` | md5sum

```

Note that your device may be different than '/dev/scd0'.

-------------------------------------------------------------------------------

2. Compare the files on CD to the files in the ISO.

Loop mount the ISO:

```

$ sudo mount -o loop -t iso9660 filename.iso /mnt/iso

```

Note that directory '/mnt/iso' may need to be created.

Run 'diff -r' to find any differences.

```

$ diff -r /media/cdrom0 /mnt/iso

```

Note that '/media/cdrom0' may be different on your machine.

If the output is empty, then there are no differences.

-------------------------------------------------------------------------------

Anyway, that's the way I do it on Hardy.

HTH

---

### Post by openfreak on 2009-03-30
hi azc
Thanks for the reply. the second option seems better since time an hdd space is not wasted in generating iso from the disk.

Thanks again

---

### Post by azc on 2009-03-30
You're welcome :)

One thing, though - the first option does not create another file on the HD.

It simply calculates the CD MD5SUM on the fly.

---

