---
title: "Recent install, no longer boots"
date: 2008-12-08
forum: General Help
---

### Post by JAJB92 on 2008-12-08
I installed Ubuntu yesterday, my first time trying any Linux whatsoever, and resolved an issue I had with ownership of one of my hard drives.

Today, after being on for a short amount of time, downloading updates and a couple of files (.rar files), I noticed my hard drive that I was having an issue with was not displaying any files, and saying it was "Read only".

I restarted my computer, hoping to resolve the issue, to find that it no longer boots, and gives me a long error message, which I will restart to find again once I finish writing this post.

I am currently running from a live disk.

I am hoping someone can shed some light on this problem, because to my knowledge I did not change any essential files.

---

### Post by JAJB92 on 2008-12-08
Update: It seems to run all the normal boot stuff except it does this: 

CLIENT MAC ADDR: 00 04 4B 06 5F DD GUID: 669A0C20-0008-46A7-DA11-FDAG807EDEC6
DHCP......

And stops there with a spinning /.

---

### Post by albinootje on 2008-12-08
> CLIENT MAC ADDR: 00 04 4B 06 5F DD GUID: 669A0C20-0008-46A7-
> DA11-FDAG807EDEC6

This is an attempt from your computer to boot over the network.
It could be that your hard disk is not found, and that this is the last booting attempt.
But if your hard disk is found in the BIOS, make sure it will try booting from the hard disk before trying to boot over the network.
Can you try this from within the Live-cd in a terminal :
dmesg|grep hd
dmesg|grep sd
to see whether your hard disk is still alive ?

---

### Post by JAJB92 on 2008-12-08
ubuntu@ubuntu:~$ dmesg|grep hd
[    4.120555] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[   47.039322] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
ubuntu@ubuntu:~$ dmesg|grep sd
[    5.815572] Driver 'sd' needs updating - please use bus_type methods
[    5.816209] sd 1:0:0:0: [sda] 156312576 512-byte hardware sectors (80032 MB)
[    5.816232] sd 1:0:0:0: [sda] Write Protect is off
[    5.816235] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.816271] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.816348] sd 1:0:0:0: [sda] 156312576 512-byte hardware sectors (80032 MB)
[    5.816368] sd 1:0:0:0: [sda] Write Protect is off
[    5.816371] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.816408] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.816413]  sda: sda1
[    5.825560] sd 1:0:0:0: [sda] Attached SCSI disk
[    5.969302] sd 4:0:0:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[    5.969324] sd 4:0:0:0: [sdb] Write Protect is off
[    5.969327] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.969363] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.969437] sd 4:0:0:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[    5.969457] sd 4:0:0:0: [sdb] Write Protect is off
[    5.969460] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.969496] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.969501]  sdb:<3>ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    6.555692] sd 4:0:0:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[    6.555721] sd 4:0:0:0: [sdb] Write Protect is off
[    6.555726] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.555774] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.555822] sd 4:0:0:0: [sdb] 398297088 512-byte hardware sectors (203928 MB)
[    6.555855] sd 4:0:0:0: [sdb] Write Protect is off
[    6.555858] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.555890] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.555905]  sdb1
[    6.556024] sd 4:0:0:0: [sdb] Attached SCSI disk

---

