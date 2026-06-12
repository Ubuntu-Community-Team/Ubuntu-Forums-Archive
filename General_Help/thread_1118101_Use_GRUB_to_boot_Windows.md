---
title: "Use GRUB to boot Windows"
date: 2009-04-06
forum: General Help
---

### Post by camper365 on 2009-04-06
I have been using Ubuntu for a while now, and I decided to delete the Windows partition to get the free space in Ubuntu. However, before I deleted the partition, I copied my entire Windows hard drive to an External Hard Drive.
I soon regretted deleting Windows, so I repartitioned my hard drive to put the NTFS back and copied the files back to my Windows partition. How do I make GRUB boot Windows?

I have found the commands root, chainloader, and makeactive. However, it tells me that I have an unrecognized device (I think it was Error 12). I made Windows the first partition of the first disk.

---

### Post by SuperSonic4 on 2009-04-06
If windows works then you'll need to add something to grub like

```
# (2) Windows
title Windows
root (hd0,0)
makeactive
chainloader +1
```

(hd0,0) is the first partition on the first hard drive

---

### Post by coffeecat on 2009-04-06
You must edit the grub menu. From a terminal, thusly:

```
gksudo gedit /boot/grub/menu.lst
```You say you have installed Windows to the first partition of the first drive, so put in this stanza, probably right at the end is best:

```
title       Windows
rootnoverify    (hd0,0)
savedefault
chainloader    +1
```**or**

```
title        Windows
root        (hd0,0)
makeactive
chainloader    +1
```They both work; they're both from different Ubuntu menu.lst files as set up by the installer.

Now save the file.

You might need to set the boot flag of sda1. Windows needs the boot flag set. Either install Gparted for this which you'll find at System > Administration > Partition Editor after you've installed it. Or, if you don't want to install it, boot up the live CD and you'll find Gparted in the same place.

**Edit:** I've just noticed you said that you copied Windows from one disc to another and then back again. If you did a straight drag and drop copy of Windows, it almost certainly won't work. You'll have to reinstall, but if you reinstall, the Windows installer will overwrite grub stage 1 in the mbr and you'll only be able to boot into Windows. But that's all right - it's easy enough to repair grub. We'll just need to know the partition number of the root partition of Ubuntu.

---

### Post by camper365 on 2009-04-13
The commands:

root (hd0,0)
makeactive
chainloader +1
boot


give you an error 12 because the makeactive and chainloader +1 are out of order.
I accidentally figured that out when I was trying to get it to work and I was doing them out of order from what this post said (I thought they were in the right order to begin with) and it worked.
You have to put the chainloader first, because makeactive makes the partition that you chainloaded active, if you haven't chainloaded a partition, then there's nothing to make active.

---

### Post by coffeecat on 2009-04-14
> **camper365 said:**
> The commands:

root (hd0,0)
makeactive
chainloader +1
boot


give you an error 12 because the makeactive and chainloader +1 are out of order.
I accidentally figured that out when I was trying to get it to work and I was doing them out of order from what this post said (I thought they were in the right order to begin with) and it worked.
You have to put the chainloader first, because makeactive makes the partition that you chainloaded active, if you haven't chainloaded a partition, then there's nothing to make active.

Hmm.... Not quite, and I don't know why makeactive before chainloader didn't work for you. See this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1
```That's the stanza for Windows that the Ubuntu installer set up for me and, yes, it does boot up Windows. The reason it boots without a boot line is because there's a title line for one of my other Linux installations immediately following. That seems to make a boot line superfluous.

Actually, you're slightly misunderstanding the makeactive/chainloader commands. As you say, makeactive makes the partition defined by the root or rootnoverify line active, but chainloader simply passes control to the Windows bootloader in the Windows partition. From the [Grub Manual]("http://www.gnu.org/software/grub/manual/grub.html").

> 
**4.1.2 Load another boot loader to boot unsupported operating systems**

  If you want to boot an unsupported operating system (e.g. Windows 95), chain-load a boot loader for the operating system. Normally, the boot loader is embedded in the boot sector of the partition on which the operating system is installed.       

[LIST=1]
[*]Set GRUB's root device to the partition by the command rootnoverify (see [rootnoverify]("http://www.gnu.org/software/grub/manual/grub.html#rootnoverify")):                 grub> rootnoverify (hd0,0)
[*]Set the active flag in the partition using the command makeactive[6]("http://www.gnu.org/software/grub/manual/grub.html#fn-6") (see [makeactive]("http://www.gnu.org/software/grub/manual/grub.html#makeactive")):                 grub> makeactive
[*]Load the boot loader with the command chainloader (see [chainloader]("http://www.gnu.org/software/grub/manual/grub.html#chainloader")):                 grub> chainloader +1
           `+1' indicates that GRUB should read one sector from the start of the partition. The complete description about this syntax can be found in [Block list syntax]("http://www.gnu.org/software/grub/manual/grub.html#Block-list-syntax").
[*]Run the command boot (see [boot]("http://www.gnu.org/software/grub/manual/grub.html#boot")).
[/LIST]
     However, DOS and Windows have some deficiencies, so you might have to use more complicated instructions. See [DOS/Windows]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows"), for more information.Have a look at the grub link to be able to read that section properly formatted. It makes better sense that way.

---

