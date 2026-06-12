---
title: "Restoring the Windows Bootloader"
date: 2009-06-04
forum: General Help
---

### Post by yoman82 on 2009-06-04
I'm sorry, I truly do love Ubuntu, but I've got to remove it from my basement computer. Currently, Ubuntu is installed on a slave 40GB drive, and Windows on an 80GB one. I need more space for another HDD, and I have Windows programs I MUST be able to run, programs not runnable in Wine. The choice I have come to is to remove the Ubuntu drive. Unfortunately, this means GRUB must go, too, but I have no idea how to get Windows to boot without it, since it overwrote the other loader. How do I repair the original, Windows bootloader WITHOUT an original Windows install disc? Thank you for the help, and I still will use Ubuntu daily on my laptop.

---

### Post by baseface on 2009-06-04
> **yoman82 said:**
> I'm sorry, I truly do love Ubuntu, but I've got to remove it from my basement computer. Currently, Ubuntu is installed on a slave 40GB drive, and Windows on an 80GB one. I need more space for another HDD, and I have Windows programs I MUST be able to run, programs not runnable in Wine. The choice I have come to is to remove the Ubuntu drive. Unfortunately, this means GRUB must go, too, but I have no idea how to get Windows to boot without it, since it overwrote the other loader. How do I repair the original, Windows bootloader WITHOUT an original Windows install disc? Thank you for the help, and I still will use Ubuntu daily on my laptop.
 
you can use *fixmbr *in windows to get your windows loader back.

---

### Post by ajgreeny on 2009-06-04
[Supergrub]("http://supergrub.forjamari.linex.org/?section=download") will be able to get you back to a windows MBR.

---

### Post by yoman82 on 2009-06-04
> **baseface said:**
> you can use *fixmbr *in windows to get your windows loader back.

Where would this program be located?

---

### Post by logos34 on 2009-06-04
> **yoman82 said:**
> Where would this program be located?

it's on the XP install CD>'R' Recovery Console>at prompt type **fixmbr**

or use [this method]("http://ubuntuforums.org/showpost.php?p=4691608&postcount=2")

---

### Post by lindsay7 on 2009-06-04
See this for more info 

[http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)

---

### Post by jbruced on 2009-06-04
Sorry you have no Windows CD(not really). Did you lose it ;-)


Maybe use gparted, resize Ubuntu very small, then make new partition with extra space, and format as ntfs. All using Ubuntu!

You'll still have grub and Ubuntu, and nothing will break!

---

### Post by yoman82 on 2009-06-04
I have Ubuntu on a separate PHYSICAL DRIVE, and only two bays in my computer. I need to install a new drive, so Ubuntu has to go. I got a crappy OEM computer that lacked a CD, so...
I guess I'm sticking with Super GRUB.

---

### Post by logos34 on 2009-06-04
oh, i didn't see where you said WITHOUT a cd...Yeah, they don't make it easy, you're lucky if oem machine comes with 'recovery' partition (never mind the fact that you're *paying* for windows)...Super Grub will do the job, but if you ask me the menus are hopeless confusing.

The best way in my opinion was the old DOS boot floppy.  **fdisk /mbr**...done.  But who has floppies anymore?

---

### Post by raymondh on 2009-06-04
> **yoman82 said:**
> I have Ubuntu on a separate PHYSICAL DRIVE, and only two bays in my computer. I need to install a new drive, so Ubuntu has to go. I got a crappy OEM computer that lacked a CD, so...
I guess I'm sticking with Super GRUB.

Supergrub's ok.

[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

Regards,

---

