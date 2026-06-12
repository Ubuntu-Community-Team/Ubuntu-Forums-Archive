---
title: "Moved linux partition.. no more free space"
date: 2009-03-15
forum: General Help
---

### Post by steevz on 2009-03-15
So I deleted an old windows partition and gave Linux it's own drive. 200GB instead of the 80GB partition I had on my other drive running linux.

After I copied and extended my linux partition added a linux swap and made the new partition bootable, it still only shows that I have 43GB of free space available to linux, where it should be more like 150GB.

If anyone knows what might be happening and how I can get linux to see the free space that should be right in front of it, that would be great.

Thanks in advance.

steevz

---

### Post by Altay_H on 2009-03-15
What are you using to partition your drive? I'd suggest Gparted just to be sure your partition editor isn't what's causing the problems.

It sounds to me like to removed one partition, but the space that was freed up by removing that partition is still unallocated. If this is the case you need to extend your linux partition to fill up the unallocated space before you can start using it.

You won't be able to expand a partition that is mounted, so you'll most likely need to boot via LiveCD to edit your linux partition.

---

### Post by steevz on 2009-03-15
I booted in to the Gparted live cd and I copied over the linux partition and extended it to allocate all the space. It is booting from this new drive as well. I'm confused.

---

### Post by Altay_H on 2009-03-16
> **steevz said:**
> I booted in to the Gparted live cd and I copied over the linux partition and extended it to allocate all the space. It is booting from this new drive as well. I'm confused.
Oh. My assumption was incorrect. In that case you should have all the space you allocated. I can't imagine why you wouldn't. Hopefully someone else here can be helpful.

---

### Post by ugm6hr on 2009-03-16
Not really sure what you've done, but perhaps a couple of commands will provide us with the necessary detail:

```
df -h
sudo fdisk -l
```

---

### Post by steevz on 2009-03-16
df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5              84G   46G   35G  57% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  208K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.8M  2.0G   1% /dev
tmpfs                 2.0G  104K  2.0G   1% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdc1             466G  355G  112G  77% /media/THATS A HUGE BITCH

```

sudo fdisk -l
```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23786   191061013+  83  Linux
/dev/sda2           23787       24321     4297387+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0ccc0cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       27340   219608518+   7  HPFS/NTFS
/dev/sdb2           27341       38913    92960122+   f  W95 Ext'd (LBA)
/dev/sdb5           27341       38437    89136621   83  Linux
/dev/sdb6           38438       38913     3823438+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

```

I should be booting from /dev/sda1.

My old partition is /dev/sdb5.

When Ubuntu boots it says from (hd0,0).

Anyone know what's going on here?

steevz

---

### Post by ugm6hr on 2009-03-16
Nope.

You have /dev/sdb5 mounted as the root directory (as seen in df):
```
**/dev/sdb5 **             84G   46G   35G  57% /
```

In fact, sda1 is not mounted at all.

Not sure how you installed, but whichever HD is your first boot device (presumably sdb) has a grub menu.lst entry that points to sdb5.

---

### Post by steevz on 2009-03-16
How do I fix this?

---

### Post by steevz on 2009-03-16
Tried modifying the grub configuration with:

sudo grub
root (hd0,0)
setup (hd0)

Still getting same result.

Anyone else have any ideas?

---

### Post by ugm6hr on 2009-03-17
Try changing the boot priority in BIOS.

Did you actually install Grub on sda MBR?

---

### Post by steevz on 2009-03-17
I tried. I used the command line in the grub loader with the commands:

```

root (hd0,0)
setup (hd0)

```

It booted the proper partition and I was so happy, after booting to windows it has
reverted back to my small partition on Linux. I enter those commands in the grub
command line again and it didn't work this time.

I change boot priority in BIOS and Windows just boots straight up.

I'm stumped.

---

### Post by steevz on 2009-03-17
How do I install sda to my MBR exactly?

---

### Post by steevz on 2009-03-17
Just found out my uuid's in my menu.lst are pointing to hd0,0 where the new linux parition is. So it should be set up correctly. Plus it says it's booting to (hd0,0) ext3 when booting up but it goes to the old install instead.

How do I get it to mount /dev/sda1 instead of /dev/sdb4/ and boot from it?

---

### Post by steevz on 2009-03-18
Just formated and did a clean install instead of copy and it's working fine. Thanks to who ever tried to help.

---

