---
title: "swap partition not mounting"
date: 2012-09-05
forum: Desktop Environments
---

### Post by dsikl on 2012-09-05
Hey people, I'm having trouble with my swap partition, it won't mount. I'd read this thread: [http://ubuntuforums.org/showthread.php?t=1462909&highlight=swap+partition]("http://ubuntuforums.org/showthread.php?t=1462909&highlight=swap+partition") and followed those instructions, but my swap seems to get a different UUID every time I boot up. Not kidding :)

Can anyone help me out? I'm running a fresh install of lubuntu on amd64 machine, everything else is perfect, I even tried reformatting swap booting up into gparted, but that obviously didn't help either (that was before I read the thread above). Any suggestions would be much appreciated!

Cheers!

---

### Post by Bobhuber on 2012-09-05
> **dsikl said:**
> Hey people, I'm having trouble with my swap partition, it won't mount. I'd read this thread: [http://ubuntuforums.org/showthread.php?t=1462909&highlight=swap+partition](http://ubuntuforums.org/showthread.php?t=1462909&highlight=swap+partition) and followed those instructions, but my swap seems to get a different UUID every time I boot up. Not kidding :)

Can anyone help me out? I'm running a fresh install of lubuntu on amd64 machine, everything else is perfect, I even tried reformatting swap booting up into gparted, but that obviously didn't help either (that was before I read the thread above). Any suggestions would be much appreciated!

Cheers!
You most likely have changed the UUID by reformating the partition. Run BLKID from a terminal as root and make sure the UUID matches what you see in fstab. Once set it will not change unless you change the partition in some way.Not kidding.

---

### Post by dsikl on 2012-09-06
Hey thanks for your reply! I really appreciate it ):P

ok, let's try this:

sudo blkid
/dev/sda1: UUID="ef7c1a95-f36e-496d-9cfb-652d04883f5e" TYPE="ext2" 
/dev/sda6: UUID="e256e84e-40eb-4a12-8d34-a44f75106413" TYPE="ext4" 
/dev/sda7: UUID="551ce3bd-3f00-44d2-a79a-4e11797064b0" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="[COLOR="Red"]f85e7bb2-b5f7-4d75-b940-69cda117efe1[/COLOR]" TYPE="swap" 

so it's [COLOR="red"]f85e7bb2-b5f7-4d75-b940-69cda117efe1[/COLOR]


cat /etc/fstab |grep swap
# swap was on /dev/sda5 during installation
#UUID=[COLOR="red"]0517bf50-2122-4e44-9f6a-fa5415fce7ca[/COLOR] none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

and here it's [COLOR="red"]0517bf50-2122-4e44-9f6a-fa5415fce7ca[/COLOR]

and it should be the one above, right? the [COLOR="red"]f85e7bb2-b5f7-4d75-b940-69cda117efe1[/COLOR]

so I gksudo gedit /etc/fstab and I find the line and it matches the [COLOR="red"]0517bf50-2122-4e44-9f6a-fa5415fce7ca[/COLOR], and I change it to [COLOR="red"]f85e7bb2-b5f7-4d75-b940-69cda117efe1[/COLOR] and save the file

now I sudo swapon -a and nothing happens in the terminal, other than accepting the command silently :) and so I suppose that should be it, right?

and now I check sudo blkid again, and I cat /etc/fstab |grep swap and they match!

ok, last time I started gparted to see if it were mounted now, and it wasn't but I won't do that now, let me just restart and I'll let you know the results

---

### Post by dsikl on 2012-09-06
sudo blkid
/dev/sda1: UUID="ef7c1a95-f36e-496d-9cfb-652d04883f5e" TYPE="ext2" 
/dev/sda6: UUID="e256e84e-40eb-4a12-8d34-a44f75106413" TYPE="ext4" 
/dev/sda7: UUID="551ce3bd-3f00-44d2-a79a-4e11797064b0" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="[COLOR="Red"]d84eb502-7031-4b6c-891a-00e313153435[/COLOR]" TYPE="swap"

it's different now isn't it?

we had [COLOR="red"]f85e7bb2-b5f7-4d75-b940-69cda117efe1[/COLOR]
and now we have [COLOR="Red"]d84eb502-7031-4b6c-891a-00e313153435[/COLOR]


cat /etc/fstab |grep swap
# swap was on /dev/sda5 during installation
#UUID=[COLOR="Red"]f85e7bb2-b5f7-4d75-b940-69cda117efe1[/COLOR] none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

so fstab hasn't changed since I changed it before boot, the other one changed (the UUID?) :(

and you say that doesn't change, unless I manipulate the partition somehow.......and it changes during boot, so it's likely the partition gets manipulated during boot, isn't it?

alright, let me boot again, and if it changes again, I guess we'll be sure about that at least

---

### Post by dsikl on 2012-09-06
sudo blkid

/dev/sda1: UUID="ef7c1a95-f36e-496d-9cfb-652d04883f5e" TYPE="ext2" 
/dev/sda6: UUID="e256e84e-40eb-4a12-8d34-a44f75106413" TYPE="ext4" 
/dev/sda7: UUID="551ce3bd-3f00-44d2-a79a-4e11797064b0" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="[COLOR="Red"]2aaf2b35-686c-4e83-881d-da4a1d5b9e06[/COLOR]" TYPE="swap" 

I seriously have no idea what this is all about, but I would really appreciate any ideas!

cheers!

---

### Post by marinara on 2012-09-06
why you using the crypt swap?  do you just want a swap partition?

---

### Post by wheeze on 2012-09-06
The UUID you're using is for the cryptswap partition yet you're entering it in the fstab listing for the regular swap partition, which is commented out and won't have any effect anyway.

I'm not familiar with cryptswap but I'm guessing that it changes the UUID at every boot due to some encryption activity its performing?

Your cryptswap partition is listed by name in fstab so the UUID it has doesn't matter. I'd suggest this is a cryptswap configuration issue.

---

### Post by dsikl on 2012-09-07
good morning everyone :) well...good question! no idea :)

that was the only swap listed that I could find, and yeah, I understand your point, but what did I do wrong or where did I go wrong to end up with only cryptswap and not a normal swap as well? I can't recall encrypting my partitions during install... after all, the other partitions are not encrypted.

cheers!

---

### Post by dsikl on 2012-09-07
and yes, I just want a swap partition...

---

### Post by marinara on 2012-09-07
i'm not going to go into creating a swap partition with fdisk, you can use gnome disks, just create a parittion of type "swap"
then do something like this
 snip@snip:/dev/disk/by-uuid$ ll
total 0
drwxr-xr-x 2 root root 100 Sep  5 17:59 ./
drwxr-xr-x 6 root root 120 Sep  5 17:59 ../
lrwxrwxrwx 1 root root  10 Sep  5 18:00 743999c2-d0bd-4cef-8bc5-147b7dc6111c -> ../../sda5
lrwxrwxrwx 1 root root  10 Sep  5 18:00 8cc901bf-cf6e-4738-bade-741c221db9fc -> ../../sda1
lrwxrwxrwx 1 root root  10 Sep  5 18:00 cf1b16b7-69af-43ea-ba51-adc381df56aa -> ../../sda6
snip@snip:/dev/disk/by-uuid$

---

### Post by dsikl on 2012-09-07
ok, I don't think I need to create a swap partition, it got created during the installation, it just won't mount, right?

[IMG]https://dl.dropbox.com/u/103678576/2012-09-07-210952_1680x1050_scrot.png[/IMG]

here's the stuff you requested:


total 0
drwxr-xr-x 2 root root 140 Sep  7 21:17 ./
drwxr-xr-x 6 root root 120 Sep  7 21:17 ../
lrwxrwxrwx 1 root root  10 Sep  7 21:17 0A9810FD9810E8C9 -> ../../sdb1
lrwxrwxrwx 1 root root  10 Sep  7 21:17 4d9fb9d9-86a7-4818-861f-f57076b1f89f -> ../../dm-0
lrwxrwxrwx 1 root root  10 Sep  7 21:17 551ce3bd-3f00-44d2-a79a-4e11797064b0 -> ../../sda7
lrwxrwxrwx 1 root root  10 Sep  7 21:17 e256e84e-40eb-4a12-8d34-a44f75106413 -> ../../sda6
lrwxrwxrwx 1 root root  10 Sep  7 21:17 ef7c1a95-f36e-496d-9cfb-652d04883f5e -> ../../sda1

here's another interesting thing I noticed while editing fstab once: my / partition is reporting mounting errors or at least difficulties, do you think that could be connected?

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=e256e84e-40eb-4a12-8d34-a44f75106413 /               ext4    [COLOR="Red"]errors=remount-ro[/COLOR] 0       1
# /boot was on /dev/sda1 during installation
UUID=ef7c1a95-f36e-496d-9cfb-652d04883f5e /boot           ext2    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=551ce3bd-3f00-44d2-a79a-4e11797064b0 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
#UUID=1cb6a555-e90d-45a1-be0a-ad75df0a27c3 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

---

### Post by Bashing-om on 2012-09-07
if I may intercede, check for encrypted partitions: 
```

sudo dmsetup status

```hopefully the output is: No devices found

else: perhaps Gparted to delete the partition (live cd swap turned off) .. and Gparted to add the partition back ??

Then: update fstab by deleting the erroneous cryprswap1 entries and inserting the correct line , Here is mine to use (change sda5 and uuid).
# swap was on /dev/sda5 during installation
UUID=5600e3b4-ca64-4836-a1cc-86d5b763346d none            swap    sw              0       0

[INDENT]HTH<==BDQ
[/INDENT]

---

### Post by dsikl on 2012-09-07
ah yes, that absolutely did it! :) thank you!

this is what my fstab looks like now:


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=e256e84e-40eb-4a12-8d34-a44f75106413 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=ef7c1a95-f36e-496d-9cfb-652d04883f5e /boot           ext2    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=551ce3bd-3f00-44d2-a79a-4e11797064b0 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=edb63901-68c2-4a2c-9b2f-56813be8762d none            swap    sw              0       0

(I have also removed the '#' before the swap UUID, and the sda's got all mixed up - I had to change it for /, for /home, and swap got a whole new sda7 - was I right to do so? those lines are commented out anyway and it says only what they were during install.......if I should get them back, I saved a copy!)

but can you tell me what this error in the '/' line means? is there something wrong or should I leave it as such?

And sudo dmsetup status gives me "No devices found" now.

Cheers!

---

### Post by wheeze on 2012-09-07
> **dsikl said:**
> 
UUID=e256e84e-40eb-4a12-8d34-a44f75106413 /               ext4    errors=remount-ro 0       1

but can you tell me what this error in the '/' line means? is there something wrong or should I leave it as such?

Glad you finally got it sorted, dsikl.

The errors statement in your / mount line simply tells the system that if there are any errors encountered during mounting that partition, it should remount it as read only (ro).

EDIT: That is to say, it's a standard line for / in fstab. Leave it as it is, no worries.

---

### Post by Bashing-om on 2012-09-07
you do good work !

 Please mark thread as solved, aids others in searching for solutions.

[INDENT]regards <==BDQ
[/INDENT]

---

### Post by dsikl on 2012-09-07
beautiful!!! thank you so much! ):P

---

### Post by dsikl on 2012-10-15
Hey ppl, I'm sorry, but I'm having the same problem again :(

I installed ubuntu studio 12.04 from the scratch this time (instead of building up from lubuntu), and the issue with that swap partition came back, but I can't seem to solve it the same way this time around… It's ignoring my deleting of that crypt swap line in fstab, still mounting crypt swap... I was also wondering where the crypt swap is coming from? Does it come from me encrypting my home folders?

here's some of them outputs as before...

- sudo dmsetup status:

cryptswap1: 0 19310130 crypt

- sudo blkid:

/dev/sda1: UUID="e9515d1a-40a1-421c-bb55-c1208d6e7c8e" TYPE="ext2" 
/dev/sda3: UUID="a7a8769e-1c33-4762-8fc7-3d02b76d6916" TYPE="ext4" 
/dev/sda4: UUID="5f3a0bd4-a135-4e11-8b10-27f7b1130ec8" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="55a578cf-de6d-4438-ad46-1b2c11ec0ed9" TYPE="swap"

- cat /etc/fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=a7a8769e-1c33-4762-8fc7-3d02b76d6916 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=e9515d1a-40a1-421c-bb55-c1208d6e7c8e /boot           ext2    defaults        0       2
# /home was on /dev/sda4 during installation
UUID=5f3a0bd4-a135-4e11-8b10-27f7b1130ec8 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=08449da6-df7a-484c-8e31-75acbf512c43 none            swap    sw              0       0

- /dev/disk/by-uuid$ ll:

total 0
drwxr-xr-x 2 root root 120 Oct 15 23:56 ./
drwxr-xr-x 5 root root 100 Oct 15 23:56 ../
lrwxrwxrwx 1 root root  10 Oct 15 23:56 55a578cf-de6d-4438-ad46-1b2c11ec0ed9 -> ../../dm-0
lrwxrwxrwx 1 root root  10 Oct 15 23:56 5f3a0bd4-a135-4e11-8b10-27f7b1130ec8 -> ../../sda4
lrwxrwxrwx 1 root root  10 Oct 15 23:56 a7a8769e-1c33-4762-8fc7-3d02b76d6916 -> ../../sda3
lrwxrwxrwx 1 root root  10 Oct 15 23:56 e9515d1a-40a1-421c-bb55-c1208d6e7c8e -> ../../sda1

Any ideas how to get around it would be much appreciated!

cheers!

---

### Post by dsikl on 2012-10-16
orrite, I reinstalled my / from the scratch and went through the steps suggested by Bashing-om, and it worked this time around...

btw, I had to reinstall twice, as I didn't quite know how to reuse the /home partition with the new installation the first time around, and in doing so I decided not to encrypt my /home folders, which then created and mounted my swap partition without any problems whatsoever.........only my /home partition wasn't accessible, so I went and reinstalled, reused my old /home partition proper, and had to keep in encrypted (couldn't change that)........restarting after install gave me the old problem again (crypt swap, and my swap not mounting)..........which I was then able to solve with the help of Bashing-om's suggestions

the reason I'm saying this is because I believe the issue has to do with the encryption of the /home folders..........correct me if I'm wrong

thanks to Bashing-om again! my buntu is running smooth now :)

cheers!

---

