---
title: "&quot;Advanced&quot; partitioning questions"
date: 2006-01-19
forum: General Help
---

### Post by smaller on 2006-01-19
Yesterday my system got screwed up after the installer of windows vista renamed my partitions, this caused grub to bail out with an error 22. I managed to fix it after a lot of playing around (The Ubuntu forums were down, that was kind of painful under the circumstances) , but the whole situation made me realise that I don't know nearly as much as I thought I knew about this subject. So here are some questions, I hope you guys can help me out...

[LIST=1]
[*]How do I find out the grub names of partitions? I know that in the format (hd0,0) the first 0 represents your first hard drive and the second 0 represents your first partition on that drive. But what exactly does "first" mean? In my case for example my first hard drive is not hda but hdc, and the first partition on that drive, hdc1 is not the one starting at block 1. 


[*]Suppose you don't know your hardware and you start with the live cd so the disks are not mounted yet. Is there a way to find out which hard drives and partitions are available?


[*]I currently have an empty space before my first partition hdc1, if I partition that space with the vista installer then the new partition will be named hdc1 and my current hdc1 will be renamed (to for example hdc3, but you have no control over it unfortunately). On the other hand if I partition this empty space with Linux (with gparted for example) then the new partition will be named hdc3 and hdc1 simply keeps it name. Is there a way to rename partitions under linux, like the vista installer does? I don't like the fact that hdc1 is not starting at block 1 on my system at the moment. (I know I can move the partition, but that's not what I want to achieve)


[*]Am I right in thinking that "renaming" partitions (see 3) is nothing more then changing the order in which they are specified in the partitioning table? 


[*]I currently have a logical partition with 1 linux swap partition inside and a chunk of empty space. I would like to remove the logical partition and just have a plain swap partition. How do I go about this? I have noticed that both partitions are locked if I start up with the live cd, does the live cd use that swap space? On the other hand if I boot my system normally I can delete the swap space, but not the logical partition, does this mean my normal boot does NOT use this swap space? That is really strange, I suspect my system will crash and burn if I delete the swap partition this way. Or will ubuntu still boot without the swap partition?
test
[/LIST]

I'd be really grateful if someone could answer these questions. If you want or can answer just one then that's fine too, just mention which question you are answering, it's clearer for everyone. :)

---

### Post by Azion on 2006-01-19
First would mean, the first drive that your PC detects. Should be number one in the bios.

Not 100% on what you mean, but I think fdisk would give you the info you need.

I don't think there is a way of renaming partitions. What it seems to me is that Vista is simply changing the "Drive Letter" of the partitions, I think that's what you mean.

Kinda of, it's more the drive letters than the actual partition names.

Delete the logical partition and resize the swap to take up the rest of the space.

---

### Post by jnoreiko on 2006-01-19
[QUOTE=smaller]Suppose you don't know your hardware and you start with the live cd so the disks are not mounted yet. Is there a way to find out which hard drives and partitions are available?[/QUOTE]

Disks Manager (under system prefs) or Gparted (on some live CDs but not all)

---

