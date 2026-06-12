---
title: "It doesn't boot"
date: 2009-01-05
forum: General Help
---

### Post by jsroth on 2009-01-05
Hi,

I was using a Live USB-stick with debian after that my ubuntu refuses to boot and gives me ```
kinit: trying to resume from /dev/sda5
kinit: No resume image, doing normal boot...
init: Error parsing configuration: no such file or directory
[...] Kernel panic - not syncing: Attempted to kill init!
```
I (hope) that I haven't done anything too bad, but I'm not sure what could have caused this and how I can change it. 

e2fsck, fsck and badsectors didn't help :( can you help me? :confused:

---

### Post by ccheath on 2009-01-05
I would suggest you boot to a ubuntu live cd and try and check the bootloader to see if it's been messed with by debian live

make sure that the partition your ubuntu is on is sda5 

sounds like the ubuntu is now trying startup using the same config that the debian live was using (i bet sda5 is the usb slot you were using - hda0 if you have ide drives or sda0 if you have sata should be the norm for an install partition)

---

### Post by jsroth on 2009-01-06
I checked out /boot/grub/menu.lst it says
```
title           Ubuntu 8.10, kernel 2.6.27-9-generic
uuid            b1b45d68-5c49-4a2c-9932-d4c6711ab743
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=b1b45d68-5c49-4a2c-9932-d4c6711ab743 ro quiet splash
initrd          /boot/initrd.img-2.6.27-9-generic

title           Ubuntu 8.10, memtest86+
uuid            b1b45d68-5c49-4a2c-9932-d4c6711ab743
kernel          /boot/memtest86+.bin
quiet

```
The uuids of the memtest and the normal kernel are the same (checked that the uuid is /dev/sda2, where /boot/ is) and memtest boots without any problems whilst ubuntu still crashes. Therefore the main problem should not be the bootlaoder, right?

Maybe some more error messages are going to help you:
```

Begin Running /scripts/local-premount
19+0 records in
19+0 records out
kinit name_to_dev_t (/dev/sda5)=dev(8,5)
kinit: trying to resume from /dev/sda5
kinit: No resume image, doing normal boot...
Done.
[...] kjournald starting commit interval 5 sec.
[...] ext-3-FS mounted filesystem with ordered data mode
Begin running /scripts/local-bottom
Done.
Done.
Begin running /scripts/init-bottom
Done.
init: Error parsing configuration: no such file or directory
[...] Kernel panic - not syncing: Attempted to kill init!

```

Does this help anybody? I don't know waht to do at the moment :confused:

---

### Post by ccheath on 2009-01-06
try looking here:

/boot/grub/grub.conf

---

### Post by jsroth on 2009-01-07
There's no /boot/grub/grub.conf :(
```
/boot/grub# ls
default        installed-version  menu.lst.save      stage1
device.map     jfs_stage1_5       minix_stage1_5     stage2
e2fs_stage1_5  menu.lst           reiserfs_stage1_5  xfs_stage1_5
fat_stage1_5   menu.lst~          splashimages

```

:(

---

### Post by ccheath on 2009-01-07
ok... first i just noticed that there's a menu.lst~ file

*reference:* [http://ubuntuforums.org/showthread.php?t=42524](http://ubuntuforums.org/showthread.php?t=42524)

that ~ means that it's the most recent version that was auto saved

possibly take a look at the differences between menu.lst and menu.lst~

i might just backup your menu.lst and then rename menu.lst~ to menu.lst

if that doesn't work try this:

[http://ubuntuguide.org/wiki/Dapper#How_to_change_default_Operating_System_boot-up_for_GRUB_menu](http://ubuntuguide.org/wiki/Dapper#How_to_change_default_Operating_System_boot-up_for_GRUB_menu)

basically it says to backup menu.lst then find the 

> default      0
 
section and replace it with

> default      X_sequence

i've never heard of this before, but i'd give it a shot after trying my first suggestions



if these don't solve your problem i'd wager that it's not a problem with the boot loader

---

### Post by jsroth on 2009-01-09
Thanks a lot for your help ccheath but I had to reinstall ubuntu :(

Anyways ... now it's working again

---

### Post by ccheath on 2009-01-09
Glad you got it fixed... one thing that i noticed looking for solutions to this is that just about everyone who had the same problem as you fixed it by re-installing... 

cheers,
chris

---

