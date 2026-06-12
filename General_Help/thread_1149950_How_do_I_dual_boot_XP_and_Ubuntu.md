---
title: "How do I dual boot XP and Ubuntu?"
date: 2009-05-05
forum: General Help
---

### Post by the_fury on 2009-05-05
This question has probably been answered a million times, but I'd appreciate it if you'd answer it.... a million and ONE times. =)

I know that XP uses the ntfs filing system, while ubuntu uses fat32. I've changed this in GParted - I have an entire partition that is ntfs.

My CD works - because I've been able to create a VirtualBox with it with no errors.

When I try to install XP, it says that "Windows cannot detect your hard drive".

Could someone explain this to me / help me get it to work? Thanks a lot.

---

### Post by Grenage on 2009-05-05
SATA drives?  Windows XP doesn't come with many disk drivers, unless you slipstream them.  You might also get a few headaches installing XP after ubuntu, rather than the other way around.  Alas XP's bootloader isn't quite up to grub standards.

---

### Post by prem1er on 2009-05-05
Ubuntu does not use fat32 file system. You probably meant ext3.  Honestly there is no need to answer this post there are like 30 tutorials on the net with a google search.  

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

If you have xp installed simply boot an ubuntu live cd.  Resize your partition for a /home, /, and swap.  And install ubuntu on that partition.

---

### Post by the_fury on 2009-05-05
> **prem1er said:**
> Ubuntu does not use fat32 file system. You probably meant ext3.  Honestly there is no need to answer this post there are like 30 tutorials on the net with a google search.  

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

If you have xp installed simply boot an ubuntu live cd.  Resize your partition for a /home, /, and swap.  And install ubuntu on that partition.

yes, that would be the problem - I would like to install XP with an existing ubuntu installation. Any solutions?

---

### Post by the_fury on 2009-05-05
> **Grenage said:**
> SATA drives?  Windows XP doesn't come with many disk drivers, unless you slipstream them.  You might also get a few headaches installing XP after ubuntu, rather than the other way around.  Alas XP's bootloader isn't quite up to grub standards.

Then they're aren't any ways to install XP with a pre-existing Ubuntu?

---

### Post by the_fury on 2009-05-07
Bump...

This is exactly what I mean - No one can show me any way to install XP after having installed Ubuntu. Is it even possible?

---

### Post by Bakerconspiracy on 2009-05-07
There are ways. The way I used to do it was windows first on a small predetermined space on the harddrive. That way, once you install ubuntu you don't have to do any work as far as the bootloader. 

What kind of Windows CD are you loading from: the one that came with your computer, or a retail? How are you booting to it? Let me know some general information about your setup (like motherboard and harddrive configuration) and what you have tried to do, and I / We can possibly help.


Anyways, I think a better alternative would be to use wine for the windows programs you need to use. Let me know if you would like to do that.

Also, there are a million tutorials online for this lol.

---

### Post by Dex73 on 2009-05-07
You may try to backup your Ubuntu and then install Windows over everything and then partition and install Ubuntu.

---

### Post by mprentice84 on 2009-05-07
If you all ready have a NTFS partition set aside for XP it shouldn't be a problem unless you have SATA drive(s) on your machine which a default XP install disk won't pick up (drive won't show up).  If you have the XP disk that came with your machine just select the NTFS partition that appears in the XP installation menu.  It is possible that XP will override GRUB during the installation but that is an easy fix and we can go there if we need to later.

---

### Post by the_fury on 2009-05-11
> **mprentice84 said:**
> If you all ready have a NTFS partition set aside for XP it shouldn't be a problem unless you have SATA drive(s) on your machine which a default XP install disk won't pick up (drive won't show up).  If you have the XP disk that came with your machine just select the NTFS partition that appears in the XP installation menu.  It is possible that XP will override GRUB during the installation but that is an easy fix and we can go there if we need to later.

I have an NTFS partition set aside for XP, but the problem is that once I get into the XP setup, it loads all the necessary files, then after the introduction, the setup informs me that it cannot find any hard drives (...?).

I'm so confused... I don't know whether it's not detecting my HARD DRIVE in general, or that I didn't partition the hard drive correctly...

I used GParted to format the partition... I wonder if I did it wrong....

---

### Post by prem1er on 2009-05-11
If you have a SATA drive, windows will probably have a problem finding it because it doesn't have the correct drivers to do so.  If this is what you are asking about then there are ways around it, let me know.

---

### Post by the_fury on 2009-06-02
> **Bakerconspiracy said:**
> There are ways. The way I used to do it was windows first on a small predetermined space on the harddrive. That way, once you install ubuntu you don't have to do any work as far as the bootloader. 

What kind of Windows CD are you loading from: the one that came with your computer, or a retail? How are you booting to it? Let me know some general information about your setup (like motherboard and harddrive configuration) and what you have tried to do, and I / We can possibly help.


Anyways, I think a better alternative would be to use wine for the windows programs you need to use. Let me know if you would like to do that.

Also, there are a million tutorials online for this lol.

I'm using an XP recovery CD with SP2... 

And I'm not exactly sure as to the extent that you want to know about my computer... 
I'm on a Sony VAIO, model VGN-FZ240e, a 250GB hard drive, with only Ubuntu 9.04 on it as of right now...

Not sure what else you want / how to get it, please let me know and I'll be happy to supply it. Thanks for all your help.

---

### Post by the_fury on 2009-06-02
> **prem1er said:**
> If you have a SATA drive, windows will probably have a problem finding it because it doesn't have the correct drivers to do so.  If this is what you are asking about then there are ways around it, let me know.

I'm beginning to think that that is the problem - just as a test, I hooked up an external hard drive and it recognized it (the external is an IDE). So there is a way around it?

---

### Post by VMC on 2009-06-02
Can you boot with Ubuntu Livecd and type the following so we don't have to guess as to your drive configuration:

```
sudo fdisk -l
```

---

### Post by the_fury on 2009-06-02
> **VMC said:**
> Can you boot with Ubuntu Livecd and type the following so we don't have to guess as to your drive configuration:

```
sudo fdisk -l
```

```

thefury@Upstairs-Laptop:~$ sudo fdisk -l
[sudo] password for thefury: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e608acb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29663   238268016   83  Linux
/dev/sda2           29664       30401     5927985    5  Extended
/dev/sda5           29664       30401     5927953+  82  Linux swap / Solaris

```

---

### Post by VMC on 2009-06-02
> **the_fury said:**
> ```

thefury@Upstairs-Laptop:~$ sudo fdisk -l
[sudo] password for thefury: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e608acb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29663   238268016   83  Linux
/dev/sda2           29664       30401     5927985    5  Extended
/dev/sda5           29664       30401     5927953+  82  Linux swap / Solaris

```
Ok, now I see what's happening. You can shrink sda1 down by say 20gb so you can then add Windows. That will be dicey though if you haven't done it before. It would best to shrink from the beginning so Windows appears happy otherwise you need to map windows.

You can't do this on a live system. Use Gparted on a livecd. Google for some examples.

---

### Post by the_fury on 2009-07-21
> **prem1er said:**
> If you have a SATA drive, windows will probably have a problem finding it because it doesn't have the correct drivers to do so.  If this is what you are asking about then there are ways around it, let me know.

I'm beginning to think that this is the problem (and hopefully the _only_ problem) that is keeping me from XP. Someone mentioned something about "slipstreaming" earlier, I think? I'm not sure what this means, but I'll give you my latest partitioning scheme:

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49d8e0f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    5  Extended
/dev/sda5               1          31      248944+  83  Linux
/dev/sda6              32         517     3903763+  83  Linux
/dev/sda7           30159       30401     1951866   82  Linux swap / Solaris
/dev/sda8             518       20436   159999336    7  HPFS/NTFS
/dev/sda9           20437       30158    78091933+  83  Linux

```

As you can see, I have Ubuntu and XP partitions already set up. All that remains is getting the installation to see my disk.

Can anyone help? Thanks a bunch.

---

