---
title: "Howto install GRUB in boot partition only (no MBR)?"
date: 2009-03-08
forum: General Help
---

### Post by UranUtan on 2009-03-08
Hi,

Today is my official transition day to Ubuntu 8.10 x64 from Vista x64. Reformat + reinstall. I wanted to test what a multi boot looks like, So I re-install Vista 1st on a small partition and Ubuntu next. To make the mess worse, I have read that there is a multi boot manager named GAG [http://gag.sourceforge.net/](http://gag.sourceforge.net/) So I wanted to install GAG as multi boot manager.

Quick summary: Vista installed OK on drive 0 (sda), GAG installed OK and could launch Vista. Ubuntu installed OK on drive 1 (sdb). But GAG cannot start Ubuntu (boot sector not found or invalid)

Here is the partition layout:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x03bbacc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   212994047   106496000    7  HPFS/NTFS
/dev/sda2       213005835   935657729   361325947+  83  Linux --------> /home
/dev/sda3       935657730   976768064    20555167+   5  Extended
/dev/sda5       935657793   976768064    20555136   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2ad62ad5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    42973874    21486906   83  Linux --------> /boot
/dev/sdb2        42973875   667966634   312496380    5  Extended
/dev/sdb3       667967488   976769023   154400768    7  HPFS/NTFS
/dev/sdb5        42973938   667966634   312496348+  83  Linux --------> /MyExtraData

```

There are plenty of people having this issue and I went through many lengthy posts. Even tried Super Grub Disk but it didn't work for me. Got weird error like fstab not found, /boot/grub/menu.lst missing, etc.

At the end I booted the Live CD, mounted manually the /boot and realize that GRUB was not installed. I then installed it manually by:
```

sudo mount /dev/sdb1 /boot
sudo grub-install /dev/sdb1

```
Exited LiveCD, reboot and GRUB was installed in the MBR overwritten GAG. Then I can boot both OS.I can re-install GAG later but the cause of all these troubles is that GRUB was not installed in the boot partition. Which leads me to the question:

[COLOR="Red"]**Question: **[/COLOR] Using Desktop CD or Alternate CD to install a brand new Ubuntu x64 on a manual partition. Where, in the installation screen that I can set "Install GRUB in the boot partition, not in the MBR".

In fact, at the very last screen of the Ubuntu Desktop Installer, I clicked on Advanced button. I leave the option "Install Boot manager" checked. But in the dropdown just below (default value sda0), I replaced by /deb/sdb1

The installer then proceeded the installation for may be 30 minutes. At the end I rebooted and the Ubuntu partition was unbootable. Turned out that GRUB was not installed at all. Is it a bug of the installer or did I miss some option screen during the installation?

Thanks in advance for any help.

---

### Post by Rallg on 2009-03-08
I am not familiar with your particular bootloader. But to answer the question about placing GRUB:

When You install Ubuntu, after using the partitioner you will come to a summary scrren that tells you what the installer is about to do, just before it begins the install. Look in the lower right for an "Advanced" button. It will allow you to place GRUB on any partition. The default is (hd0,0) which is not what you want to do here. The available partions are identified (usually) by their sdX description, but you can manually type in the hdx description of you know it. Be sure you know which partition is the desired one for GRUB. Then pick it.

In the past, when I was dual-booting with Windows XP, I installed GRUB on the same partition as Ubuntu. That did not touch the MBR or the Windows boot loader at all. If I later trashed Ubuntu, Windows would never know it. How to boot Ubuntu? In XP, it was possible to add some information (reversible) on the Windows partition, without touching the MBR. That is not so easily done with Vista, though.

It was also possible to put a different GRUB (for DOS) on a bootable USB drive. If it was selected at boot time, it would transfer control to the GRUB located within the ubuntu partition. If the USB was not inserted and selected at boot time, then Ubuntu could not be booted at all.

---

### Post by UranUtan on 2009-03-08
> **Rallg said:**
> When You install Ubuntu, after using the partitioner you will come to a summary scrren that tells you what the installer is about to do, just before it begins the install. Look in the lower right for an "Advanced" button. It will allow you to place GRUB on any partition. The default is (hd0,0) which is not what you want to do here. The available partions are identified (usually) by their sdX description, but you can manually type in the hdx description of you know it. Be sure you know which partition is the desired one for GRUB. Then pick it.

That was exactly what I have done (I repleaced (hd0,0) by /dev/sdb1 (or (hd1,0), don;t remember but I know the partition where /boot is mounted). But GRUB was NOT installed at this place. Then this should be a bug of the Ubuntu installer. May be it didn't work with a 2 SATA2 drives config.

---

### Post by Rallg on 2009-03-08
If you already tried the Advanced but it didn't work, then it does indeed sound like a problem related to the 2 SATA drives. Either that, or one of the forum's two-drive users knows the magic code needed to identify the partition better. I don't

---

### Post by meierfra. on 2009-03-08
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

