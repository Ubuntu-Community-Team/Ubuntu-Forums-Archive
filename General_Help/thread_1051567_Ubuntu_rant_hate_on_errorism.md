---
title: "Ubuntu rant: hate on errorism"
date: 2009-01-26
forum: General Help
---

### Post by Stargazer989 on 2009-01-26
I've used Ubuntu long enough to know that I like it a whole lot, not love(not yet), but like. just as it is with every Operating System floating or spreading through the net, there's going to be some errors in the System that either: > A) can't be fixed/patched 
**or** 
B) really hard to fix and or spot
I'm having a **B** issue.
Ubuntu tends to go on it's own and do what it wants... when it feels like doing good and starting up fine or making it easy to fix those broken packages with unable-to-satify package's dependencies.
here are my issues at the moment:> 
*Ubuntu Intrepid on my Gateway MC7801u* starts up in low-graphics mode for no apparent reason(taking a good 3-4+ minutes to do so).> 
*Ubuntu Hardy on my eMachines T5224* receives a grub error every time the machine is shut down and a part(say a cable(power)) is removed and re-inserted/placed. error 17 is current.
(recent): Perl package has un-satisfiable packages/dependencies.
If anyone knows or has had these problems please post here with your problems or known patches/fixes. 
thank you!! :)

---

### Post by cariboo on 2009-01-26
If this is a rant I'll ask the mods to move this to the proper place if you are asking for help, some more info would help, like what type of video card your Gateway computer has.

TO give you help with your eMachine post the output of:

```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```

please use the [noparse]```

```[/noparse] tags around the output, to make it easier to read.

Jim

---

### Post by bodhi.zazen on 2009-01-26
I agree bugs are frustrating, but I am not familiar with any OS that is free of bugs.

It is a matter of how comfortable you are (or are not) with any OS and fixing / reporting them.

In general, in Ubuntu, use Launchpad for bugs and bug reports not the forums.

---

### Post by Stargazer989 on 2009-01-27
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a75e71c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3984    32001448+  83  Linux
/dev/sda2           38340       38913     4610655   82  Linux swap / Solaris
/dev/sda3           13055       38339   203101762+  83  Linux
/dev/sda4            3985        7248    26218080   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281    b  W95 FAT32
```
[cat /boot/grub/menu.lst]("http://www.stirkbin.com/50222")

the 640 is an external, mainly for Anime and such.

and this *is* a rant but it is also a cry for help. the output above is from the laptop(Gateway MC7801u). if you want the Desktop's(eMachine T5224) then i'll post that tomorrow... or as soon as someone tells me how to fix grub so i can boot the desktop. :/

---

