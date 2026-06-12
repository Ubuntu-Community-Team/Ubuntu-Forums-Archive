---
title: "NTFS mft and filesystem screwed, any suggestions?"
date: 2009-06-18
forum: General Help
---

### Post by MusicMan374 on 2009-06-18
Okay from this thread that i started earlier: [http://ubuntuforums.org/showthread.php?t=1191364](http://ubuntuforums.org/showthread.php?t=1191364)

I concluded that when I installed grub I somehow managed to be an idiot and screw over my MFT on my ntfs partition and my ntfs boot record and possibly my mbr. Ubuntu boots fine, and when I installed ubuntu I had it copy over all my user files. I still had some other files that I would like to save if at all possible. The ntfs partition is unmountable in ubuntu and let alone bootable, not even with supergrub.

Any tools or methods of recovery would be much appreciated! THanks in advance!

---

### Post by merlinus on 2009-06-18
TestDisk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)) or SystemRescueCD ([http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)), and maybe Knoppix will be able to mount your windows partition.

---

### Post by MusicMan374 on 2009-06-19
ok so after about an hour of trying different methods, I finally got testdisk on SystemRescueCD to rebuild the ntfs boot record. I rebuilt the bootrecord, then rebuilt the mft, then rebuilt the boot record again. When I view the file list with testdisk, all my files appear in the right directories and everything, looks fine, yet I still can't boot into it. But now I get a different error. Now when I try to boot into vista I get this:

```
starting up...
grub hard drive error
```

or something of the sort, like grub hard drive failure or something.

So I got somewhere, I got the mft rebuilt and it looks perfect, except i STILL can't mount it in ubuntu or knoppix.

Still shows up as USB drive and when I try to mount says can't mount file.

So naturally I tried it in terminal with the following command:

```
sudo mkdir /mnt/ntfs
sudo mount -t ntfs /dev/sda1 /mnt/ntfs

```

It didn't return an error but all i got when I went to /mnt/ntfs were the files in the images:
[IMG]http://i42.tinypic.com/2uhll6v.png[/IMG]
and then inside the boot folder are these:
[IMG]http://i43.tinypic.com/dwcjt.png[/IMG]
and inside the other folders are files with identical names, and only one file in each of the 2 folders: bootmgr.exe.mui.

I assume I MAY be getting somewhere? Suggestions?

---

### Post by MusicMan374 on 2009-06-19
And sorry for the double post but bootmgr.exe is the bootloader for vista is it not? and why does it have the .mui extension?

---

