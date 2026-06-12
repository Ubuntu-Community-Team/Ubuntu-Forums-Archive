---
title: "How do I make a Fat32 partition?"
date: 2005-08-02
forum: Desktop Environments
---

### Post by Gabbahead on 2005-08-02
I've given up on trying to mount my NTFS partitions - it just locks Ubuntu completely. 

Onto the next option: creating a shared FAT 32 drive. Apart from using the Ubuntu install CD, is there any other way to allocate free space on my drive for a FAT32 partition? Is there perhaps some kind of GUI I can use to do this because I really don't want to muck about the root terminal if I don;t have to.

---

### Post by xaque on 2005-08-02
You might want to give QtParted a try. It's at [http://qtparted.sourceforge.net/download.en.html](http://qtparted.sourceforge.net/download.en.html). I haven't used it extensively, but it looks like it's got everything you're looking for.

---

### Post by Gabbahead on 2005-08-02
I found it. Damned if I know how to install it, though.

---

### Post by Omnios on 2005-08-02
You can get Qtparted in synaptic under universe. Also you will need some plug ins for ntfs to resise your partition.

 I did something sililar and im putting a link to my old thread mind you what I did is fairly specific to my set up in that it was about the best way for my set up (easier to understand for me). Your situation might be a bit different but it will give you the general idea.

[http://ubuntuforums.org/showthread.php?t=45605](http://ubuntuforums.org/showthread.php?t=45605)

---

### Post by Takis on 2005-08-02
I would recommend you set aside the hard disk space on your computer, reboot into Windows and use Windows to create the FAT32 partition. Windows will be a lot happier about it, and naturally Ubuntu won't have any problems. I've just had some minor issues with the Linux FAT partitioner, and I think it makes more sense for Windows to create it, considering Windows knows how to do it perfectly.

---

