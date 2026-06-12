---
title: "GRUB problems with XP/Vista"
date: 2009-04-13
forum: General Help
---

### Post by Glubbdubdribian on 2009-04-13
hi, I recently installed XP on my hdd to play a game as my machine can't handle games well on vista but now i can't seem to boot into vista!

When I select my vista entry in GRUB, xp boots.
When I select my xp entry, a message comes up saying "BOOTMGR not found - press 'ctrl + alt + delete' to restart"

The entries are set to the correct partitions so i think it might have been something that the xp installation did to the bootmgr or mbr or something...

I'd really appreciate if you could please tell me what i need to do to fix this. thx very much :)

here's my partition table:

```

Device    Boot      Start         End      Blocks   Id  System
/dev/sda1              15        5113    40956928    7  HPFS/NTFS [vista]
/dev/sda2            5114        7029    15390270   af  Unknown   [osx86]
/dev/sda3   *        7030        8307    10263552    7  HPFS/NTFS [xp]
/dev/sda4            8308        9729    11422215    5  Extended
/dev/sda5            8308        9466     9309636   83  Linux
/dev/sda6            9467        9729     2112516   82  Linux swap/Solaris

```

here's my grub menu.lst:

```

title		Ubuntu 8.10
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=cd6d851a-d84b-4758-aee7-5f91437fc8e7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title 		Mac OS X 10.5.2
rootnoverify (hd0,1)
makeactive
chainloader +1

title		Vista Ultimate
root (hd0,0)
makeactive
savedefault
chainloader +1

title		Windows XP
root (hd0,2)
makeactive
chainloader +1

```

thanks again :)

---

### Post by lolol i r linux noob on 2009-04-13
can u boot into vista with command line.

---

### Post by Glubbdubdribian on 2009-04-13
no... it just boots to xp still..

---

### Post by lolol i r linux noob on 2009-04-13
it seems once xp was installed it overwrote vista's boot loader with xp's boot loader.

Their are tutorials on the web to show how to load xp with vista's bootloader. Then you will only need one windows entry in grub.

---

### Post by meierfra. on 2009-04-13
> it seems once xp was installed it overwrote vista's boot loader with xp's boot loader.

Their are tutorials on the web to show how to load xp with vista's bootloader. 

[http://neosmart.net/wiki/display/EBCD/Installing+XP+After+Vista](http://neosmart.net/wiki/display/EBCD/Installing+XP+After+Vista)

---

### Post by lolol i r linux noob on 2009-04-13
> **meierfra. said:**
> [http://neosmart.net/wiki/display/EBCD/Installing+XP+After+Vista](http://neosmart.net/wiki/display/EBCD/Installing+XP+After+Vista)

That should work.

---

### Post by Glubbdubdribian on 2009-04-13
thank you for the info - i had just gone off and found the same thing on a different [site]("http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm?page=4") lol... but thx still :)

---

