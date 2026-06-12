---
title: "How to remove Grub from a specific partition?"
date: 2022-02-26
forum: Desktop Environments
---

### Post by Mugsy323 on 2022-02-26
Once upon a time, I had Ubuntu installed to a partition that I used for a couple of years, but somehow, the bootloader was corrupted. Now, if I try to boot from that partition, all I get is a Grub CLI (a black screen with nothing but a "grub>" command prompt.) "Help" lists available commands, but they scroll by too quickly to read. :(

I abandoned it a few years back and now use a totally separate physical drive for Ubu.

**In BIOS**, it lists the old partition as "Ubuntu" on my M2 drive (I have only one.) But **neither "GParted" in Ubu nor Windows' "Disk Management" list a partition by that name.** When I try to mount it from Ubu, it comes up empty even though GParted says there's over 50GB of data on it. :confused:

Because there is data still on the partition, I do NOT want to simply wipe/format it. I just want to remove (or possibly reinstall) Grub from/to it so I can attempt to recover the data.

Ubu's "Grub Manager" utility only lets you remove Grub from the *currently active* boot partition. And no Windows utility (that I've found) gives me the ability to remove Grub on a Linux partition via Windows.

Maybe there's a way to have Grub remove itself via that CLI? Help?

TIA

---

### Post by oldfred on 2022-02-26
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)            
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

But unless drive is damaged or partition needs fsck, you should be able to manually mount the partition and backup any data you want to preserve.

---

### Post by Mugsy323 on 2022-02-26
> **oldfred said:**
> Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO

Thx for the reply.

Despite having used Ubuntu off/on since v9.03, I still feel like a Newbie. I'm not sure where to find "the pastebin link". Rather than use a LiveCD (and failing to get a working Live USB... which is always difficult with a UEFI bios), I executed the SUDO installer commands from my working install of Ubu and installed the utility directly.

I used it to create a report and the relevant portion appears to be:

```
=> Grub2 (v2.00) is installed in the MBR of /dev/sdk and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => No boot loader is installed in the MBR of /dev/sdl.

nvme0n1p1: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Windows/System32/winload.exe

nvme0n1p2: _____________________________________________________________________

    File system:       ntfs
```

IIRC, I was running Ubu installed to a partition on my nvme drive in nfts format (I use ext4 now on the newer working install) and Win7 was first on the Grub menu back then.

I don't see anywhere in the BRU that lets me select/repair a *specific* drive/partition, so I am reluctant to try to use the utility.

Let me know if you need any additional info. Thx.

---

### Post by ActionParsnip on 2022-02-26
Why do you not have a good backup that you can recover the data from?

---

### Post by oldfred on 2022-02-26
If you run Boot-Repair's report, and let it upload your info, it will give you a pastebin link. You just need to copy & paste that link.
You should also check it works to show your configuration.

The little bit you have is BIOS/MBR with grub in the MBR.
Windows then can only boot thru grub. Grub only boots working Windows, and Windows cannot be hibernated.
But newer Windows uses fast start or always on hibernation. If a Windows update turns that back on, then you have to temporarily install a Windows BIOS boot loader, fix Windows, and then restore grub.
Always have good backups, an Ubuntu live installer and the Windows repair disk as you need them all.

UEFI makes it a bit easier as it has both Windows & Ubuntu/grub boot loaders in the ESP- efi system partition, so you can always boot either system directly from UEFI.

---

### Post by Mugsy323 on 2022-02-27
Thx for the reply. I uploaded the results to Pastebin [here]("https://paste.ubuntu.com/p/zhv75h8xFT/").

My Windows-11 boot drive (no Grub) is "nvme0n1p1" (a 120GB partition on my 500gb M2 boot drive).
I *believe* the old Linux **boot** partition appears to be: "nvme0n1p3" (a tiny 100MB partition on my M2 boot drive) with the data on a much larger partition on "nvme0n1p5".
My current working Ubuntu 20 drive is "sdj1".

I don't need the boot partition that is on "nvme0n1p3" (it shouldn't be there anyway), I just need Bios to stop detecting it as a boot drive with Grub on it.

Thx.

---

### Post by oldfred on 2022-02-27
You may want to start over.
Since you have a NVMe drive, your system must be newer and UEFI boot.

Windows only installs (and works) from gpt partitioned drives in UEFI boot mode.
Windows only installs in BIOS boot mode from MBR (msdos) partitioned drives.
Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives since 2012. Users could use BIOS/MBR but that was more for older systems.  Vendors may call UEFI as BIOS, helping to confuse owners.

Your NVMe drive is gpt but has a Windows BIOS type set of partitions. Its as if when you installed Ubuntu you converted drive to gpt and added the required ESP - efi system partition for boot files.
But your other drives are all MBR. Ubuntu will install in BIOS or UEFI mode to MBR, but should be like Windows and only use gpt with UEFI. And give warnings if BIOS/MBR Windows seen, so user may not convert/break Windows.

Also Ubuntu default install only installs boot loader to first drive whether UEFI or BIOS. With any second or an external drive, you have to manually add ESP if UEFI and reinstall grub or if BIOS manually choose to install grub to that external drive. 

You can use gpt with BIOS boot of Linux installs. I have since 2010. But now only have UEFI/gpt systems except old 2006 retired laptop that is BIOS but now with gpt partitioning.

Do you want Windows? 
You would have to convert NVMe drive back to old MBR. Better to reinstall in UEFI mode long term.

Do you want to boot external drives in UEFI or BIOS boot mode.
Note that in 2020 some vendors have said all new systems will be UEFI only. So support of older BIOS drivers will not be as good. If system works ok, you are fine with BIOS, but again better to plan on conversion to UEFI boot if UEFI hardware.

You can relatively easily convert Ubuntu from BIOS to UEFI or vice-versa. Better if gpt, but even MBR will work. With UEFI you have to have the ESP whether MBR or gpt. With BIOS and gpt, you need a tiny bios_grub partition. When starting to convert to UEFI, I added both ESP & bios_grub partitions, so I could easily move drive from BIOS to UEFI. 

With Linux the difference between UEFI & BIOS is the version of grub bootloader. 

If you want UEFI boot on external drives, convert to gpt & add an ESP (FAT32). If using gparted to convert drive, it will totally erase drive. But you can use gdisk to convert, but still need good backups.

What do you want and we can make specific suggestions.
The proxy files replace grub when you use Grub Customizer.

---

### Post by Mugsy323 on 2022-02-27
Thx for the reply. I don't think UEFI is the reason why Grub won't load on that old Linux partition, but it doesn't matter since I use "MBR/UEFI Dual Mode" so I can boot old USB thumb drives when needed.

Win11 (I used 10 for about 18 months) boots fine from the nvme, and Ubu installed just fine to a different (MBR) drive on the same PC (I'm using it now.)

It will be a sacrifice, but after almost two years, I think I'm just going to just wipe the old Linux partition. I don't even recall how important any of the data on it was (I DO remember I had a MUCH better working Wine install with saved data from a number of apps I'd hate to lose, but if I've survived two years w/o them, so I guess I don't need them THAT badly.

Oh well. :) Thx.

---

### Post by grahammechanical on 2022-02-27
I readily admit that I am confused about your partition and OS setup. So, I could be saying something completely missing the point.

Do you have a working installation of Ubuntu? If so, load that version and run

```
sudo update-grub
```

Do you see a Linux kernel for the installation that loads to a Grub command line? When you next load the Grub menu you should see the broken Ubuntu installation and next in the list Advanced options for Ubuntu. Select that and then select an older kernel. That may load correctly. Or, select a kernel with recovery mode. At the recovery menu select Network to establish an Internet connection. Then select Root shell prompt and run

```
apt update
apt upgrade
```

I wonder if this broken Ubuntu is out of life since it has been a long time since you last used it. To get out of the root shell prompt type

```
exit
```

and then select resume or type

```
shutdown -h now
```

Regards

---

### Post by Mugsy323 on 2022-02-27
Thx for the reply.

I have a working install of Ubu 20, which I installed about 18 months ago when I lost my old install. Somehow, Grub was corrupted and I was never able to access the partition again.

The problem with trying to "update" Grub or run any tool like the Boot Repair Utility is that they only see my working Grub partition. Thx.

---

