---
title: "how to unmount a partition from /"
date: 2009-01-26
forum: General Help
---

### Post by LUIWOMBAT on 2009-01-26
I am desperately  in need of help.I have installed Ubuntu 8.04 on a new dell Inspiron computer I let it took 
the whole 120 Gbs on my hard hard drive.Now I am trying to regain space to install windows in half of the hard drive.when I try to create a partition for windows,it doesn't allow me.It is telling me    that the partition for Ubuntu is mounted in / and that I need to unmount it before I make changes to that partition.How can I unmount that partition from / ?  any help will be appreciated.:(:(

---

### Post by fjgaude on 2009-01-26
Well, there are many ways, but the normal way is to use the liveCD, bring it up, and then use **GParted** in the System/Administration menu to resize the drive.

You can't unmount the / partition while you are running the OS associated with the root.

---

### Post by HermanAB on 2009-01-26
You have more than one problem now.  You should have installed Windows first, since Windows will overwrite the boot loader rendering Ubuntu dead in the water.

In order to resize the Ubuntu partition, you need to boot off a CDROM either using the Ubuntu Live CD or my favourite - Knoppix.  Only when NOT booted off the HDD can you run a partition tool.

Before you start, read up elsewhere on these forums on how to repair the boot record after installing Windows so that Ubuntu will work again.

I hope that helps!

Herman

---

### Post by -kg- on 2009-01-26
> **HermanAB said:**
> You have more than one problem now.  You should have installed Windows first, since Windows will overwrite the boot loader rendering Ubuntu dead in the water.

In order to resize the Ubuntu partition, you need to boot off a CDROM either using the Ubuntu Live CD or my favourite - Knoppix.  Only when NOT booted off the HDD can you run a partition tool.

Before you start, read up elsewhere on these forums on how to repair the boot record after installing Windows so that Ubuntu will work again.

I hope that helps!

Herman

Yes, that will happen.  Check out [this thread.]("http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore")  Oh, and read down a little ways.  The terminal method is better than the original method, IMHO.

Oh, and if you need further help with partitioning operations, see:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition").

---

### Post by Bigneil on 2009-01-26
It is much easier to do windows first then use the live ubuntu cd to partition and install ubuntu.   

I am not a linux expert nor am i a pc expert, i got myself in an absolute pickle trying to set up my dual boot.

i ended up starting over with a clean install of windows then did the ubuntu.

then, you just need to make a slight adjustment so that the computer gives you time to choose which operating system you would like to boot into.

i hope this is helpful, good luck;)

---

