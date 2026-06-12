---
title: "Kubuntu Grub errors"
date: 2006-02-27
forum: Desktop Environments
---

### Post by fleshpile on 2006-02-27
Been trying out Ubuntu for the last couple weeks and love it.  Decided to give ol' Kubuntu a try so I could compare the differences, using version 5.10 for both.

Tried a dual boot (which I've done dozens of times with other flavors of Linux and Win) with 2 week old Ubuntu on 10GB Part1 and Kubuntu on 10GB Part2, sharing a 130GB Part5 and 5GB swap (drive was formatted with dual Linux boot in mind).  Installed grub to MBR.  On reboot to continue install of Kub, I got grub error 17, and wouldn't boot to either.  Used Ultimate Boot CD to boot into Ubuntu, moved some data, then tried using boot managers to fix grub (including grub).  No good, I could only get to Ubuntu (not Kubuntu at all) with UBCD.

Reformatted over Ubuntu and Kubuntu (I read that error 17 could be partition problems) and started with freshie 20GB Part1.  Reinstalled Kubuntu, but on reboot to finish install, grub error 18 and wouldn't boot. Hmm. Tried using UBCD to get into Kub but no go.  Tried to fix MBR but no good either.

Read that error 18 was because the Bios couldn't see the boot manager because it had been installed in sectors beyond the first 1024 (even though it was a new partition and the Bios was from 2002), so switched to a different drive (same size and manufacturer), formatted the whole drive to a 150 GB Part1 and 5GB swap. Reinstalled Kubuntu.  When rebooted to finish install, grub error 18, no boot.

Now, fully P.O.'d, I tried the Ubuntu reinstall.  Reformatted the Part1, installed Ubuntu and on reboot, grub 3,2,1... booted perfectly into Ubuntu. 

Anyone hear of this before?  The drives are almost brand new 160GB IDEs, set for cable select.  I checked the MD5, and it's the same.  Both CD's are the same media, same burn prog and speed, and the Kubuntu install is smooth, just the grub it installs is having probs, and it seems to be fatal in that I can't fix the MBR at all.  Any way to get around this, or anyone know why it did this?

I really want to try Kubuntu, but after 3 failed installs today I'm kinda over it for a while.   

Specs - 1GHz AMD Athlon, 1GB pc133, NVFX5200 video, Sound Blaster PCI16

Thanks for any help.

---

