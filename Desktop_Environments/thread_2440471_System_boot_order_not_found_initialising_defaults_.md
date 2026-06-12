---
title: "System boot order not found initialising defaults creating boot entry shimx64.efi"
date: 2020-04-11
forum: Desktop Environments
---

### Post by steve.clay on 2020-04-11
Hi. When I start up my desktop PC, running ubuntu 18.04, I get a message which reads:

System boot order not found. Initialising defaults. Creating boot entry "Bootnnnn" with label "ubuntu" for file "\EFI\ubuntu\shimx64.efi"

This happens each time and the number on the Bootnnnn file increases each time.
The BIOS has the order I would expect: hard drive, removable media, CD/DVD, network.

The PC is an acer M3985. There is a huge amount of stuff on setting the shimx64.efi file as trusted to boot up with but no combination of BIOS settings that I have come up with has this prompt. I did stumble somehow into a MOK manager and it did lead me to the right place - where the files are - but it is expecting some kind of certificate and I don't have one. (The machine was passed to me with Windows on and I overwrote it with a fresh install of ubuntu. This probably erased some vital mok manager files.)

Can anyone tell me how to fix the problem please?

Update to query on 16/04/2020: On the advice given below I used efibootmgr to cut down a very long list of boot files to just this output from efibootmgr:
Bootcurrent: 004
Timeout: 1 seconds
Bootorder: 0020, 004, 0002
Boot0002: Windows Boot Manager
Boot0004* UEFI WDC WD10EZEX-22KKA0
Boot0020* ubuntu

I then restarted the machine. I got the same error message with Boot0000 in the place that is incremented each time. efibootmgr shows the data below and note that the newly created Boot0000 is exactly the same as the one that already existed at Boot0020.

I left the windows boot manager in the list but it is probably just a hangover from when this machine did have windows on it. It just has Ubuntu on it now so maybe I could remove it?

I did at this stage try sudo efibootmgr --remove-dups to see if it would remove one or other of 0000 and 0020 but it doesn't remove either of them although they look identical to me.

I'm very grateful for the help received so far and would welcome any further help, thank you.

BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0000,0004,0020,0002
Boot0000* ubuntu    HD(1,GPT,2fa7e908-cb3e-4356-858d-2da2ef01fd55,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0002  Windows Boot Manager    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...t................
Boot0004* UEFI: WDC WD10EZEX-22RKKA0    PciRoot(0x0)/Pci(0x1f,0x2)/Sata(0,65535,0)/HD(1,GPT,2fa7e908-cb3e-4356-858d-2da2ef01fd55,0x800,0x100000)AMBO
Boot0020  ubuntu    HD(1,GPT,2fa7e908-cb3e-4356-858d-2da2ef01fd55,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)

I will here reinstate some info that just might be relevant:
There is a set of folders on my computer here: /boot/efi/EFI/ubuntu and this folder contains files shimx64.efi, mmx64.efi, grubx64.efi, grub.cfg and BOOTx64.CSV.
I think that this is the set of folders referred to in the error message and in efibootmgr output as "\EFI\ubuntu\shimx64.efi"

---

### Post by lvm on 2020-04-11
Paths are fine, mount point for boot disk with EFI image is /boot/efi. Check 'sudo efibootmgr' output and set the required order with -o switch.

---

### Post by steve.clay on 2020-04-14
lvm, thank you so much for the reply. I have pasted in the efibootmgr output below. The thing I don't understand is that it doesn't make any difference if I use the -o option to put 0004 first, i.e the actual device with the boot partition on - I still get exactly the same error message. Can you help at all? I remembered that the boot partition is a separate partition from the rest of the ubuntu system. It is a fat32 partition which gparted knows to be the EFI system partition. It is flagged as boot, esp.

The output does have a warning at the top, perhaps this is why it isn't working? I don't know how to fix this problem either.

Anyway here is the output:

** Warning ** : Boot001f is not UEFI Spec compliant (lowercase hex in name)
** Warning ** : please recreate these using efibootmgr to remove this warning.
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0004,0037,0020,001F,0036,0001,0003,0005,0006,0007,0008,0009,000A,000B,000C,000D,000E,000F,0010,0011,0012,0013,0014,0015,0016,0017,0018,0019,001A,001B,001C,001D,001E,0002,0021,0022,0023,0024,0025,0026,0027,0028,0029,002A,002B,002C,002D,002E,002F,0030,0031,0032,0033,0034,0035,0000
Boot0000  ubuntu
Boot0001  ubuntu
Boot0002  Windows Boot Manager
Boot0003  ubuntu
Boot0004* UEFI: WDC WD10EZEX-22RKKA0
Boot0005  ubuntu
Boot0006  ubuntu
Boot0007  ubuntu
Boot0008  ubuntu
Boot0009  ubuntu
Boot000A  ubuntu
Boot000B  ubuntu
Boot000C  ubuntu
Boot000D  ubuntu
Boot000E  ubuntu
Boot000F  ubuntu
Boot0010  ubuntu
Boot0011  ubuntu
Boot0012  ubuntu
Boot0013  ubuntu
Boot0014  ubuntu
Boot0015  ubuntu
Boot0016  ubuntu
Boot0017  ubuntu
Boot0018  ubuntu
Boot0019  ubuntu
Boot001A  ubuntu
Boot001B  ubuntu
Boot001C  ubuntu
Boot001D  ubuntu
Boot001E  ubuntu
Boot001F  WDC WD10EZEX-22RKKA0
Boot001f_BbsIndex* 
Boot0020* ATAPI   DVD A  DH16ACSH
Boot0020_BbsIndex  
Boot0021  ubuntu
Boot0022  ubuntu
Boot0023  ubuntu
Boot0024  ubuntu
Boot0025  ubuntu
Boot0026  ubuntu
Boot0027  ubuntu
Boot0028  ubuntu
Boot0029  ubuntu
Boot002A  ubuntu
Boot002B  ubuntu
Boot002C  ubuntu
Boot002D  ubuntu
Boot002E  ubuntu
Boot002F  ubuntu
Boot0030  ubuntu
Boot0031  ubuntu
Boot0032  ubuntu
Boot0033  ubuntu
Boot0034  ubuntu
Boot0035  ubuntu
Boot0036  ubuntu
Boot0037* ubuntu

---

### Post by oldfred on 2020-04-14
I do not think I have seen that many entries.
Some UEFI get overloaded or UEFI RAM gets full.

You need to house clean many old entries. Use -v option to see details on each entry, so you can see which are the same.

sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

---

### Post by lvm on 2020-04-16
Actually efibootmgr has a -D option for automated removal of duplicates. Never used it in anger though.

---

### Post by steve.clay on 2020-04-16
Hi lvm, thank you so much for replies. I have updated the post itself with the information gained by use of efibootmgr. Still have problem as explained in edit to post. Hopefully making some progress anyway.

---

### Post by oldfred on 2020-04-16
All UEFI Acer have required "trust" to boot anything other than Windows.
But default entry normally then was shown as unknown until changed by user.

Not sure if you have set trust or not?
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

### Post by steve.clay on 2020-04-16
Hi oldfred. Nice to hear from you, you were huge help to me once before! I have amended post: there is no setting anywhere in BIOS on my pc to trust a file. I have made some comments on MOK manager which appeared just now - after I tried disabling secure boot I think - but doesn't appear to solve issue. I will read all the links asap but this is just on the basis of the first one you have put up. Thanks for assistance, hugely appreciated.

---

### Post by oldfred on 2020-04-16
Acer makes the "trust" settings under other settings that are only available when you add an UEFI password. 
Never lose that password or reset to blank when done.

Some other older Acer had to update UEFI to get trust settings.
A few older posts had users downgrading UEFI, but then newer posts said updates then added it back in.

---

### Post by steve.clay on 2020-04-17
Thanks oldfred. I have looked and looked for 'other settings' - setting every conceivable thing on and off to try to find it but it is just not there. I looked for an update to the BIOS (as acer insists on calling UEFI) but could find for my machine only things going back to 2012. Two of them mentioned linux in the web page listing but I downloaded both of them and the readme pdfs were titled that they were for DOS and the instructions talk about making a DOS bootable device and running a .bat file. It all feels too scary for me - I really don't want to break the machine to fix this problem. I guess that at a push I can live with it - maybe automating the removal of surplus entries from efibootmgr or  just doing it by hand every now and then. It's a shame and clearly something has changed in an update because I didn't have this problem until recently. Is there any chance that the upcoming 20.xx release of ubuntu might fix it? Thanks again for help. Its a really complicated area and quite a bit beyond me I think.

---

### Post by oldfred on 2020-04-17
Linux updates often improve things. I saw where Intel has  some updated drivers that will even help older CPU, but that is going into the newest Linux kernel which will probably not be in Ubuntu distribution until 20.10 or one of the later 20.04.x updates.

But those improvements will not help with vendor UEFI issues.
Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. 
Even applied to IBM mainframes, but more Intel than other systems.
Both Ubuntu & Windows updated system for the issues.

---

