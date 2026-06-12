---
title: "Install hangs with &quot;partitioner&quot; @ 41%"
date: 2005-12-19
forum: Desktop Environments
---

### Post by tlongman on 2005-12-19
:( 
Hi,
I'm just now trying to install Breezy for the first time and have run into the problem of having the installation "hang" with the screen indicating "starting the partitioner" and ceasing at 41%. I've waited about twenty minutes, but the installation never proceeded any further. Rebooting ubuntu CD and trying running in different modes, e.g., expert mode, acpi=off, etc.,  made no difference (although acpi=off causes LOTS of disk thrashing and "recovery" messages before it got to the paritioner "hang" problem. No messages that I saw seemed to indicate anything was wrong before the "hang".

Hardware:
- Abit AV8 motherboard, AMD 64-bit X2 (dual core) 4200+;
- 1GB RAM, no IDE disks but two DVD recorders, Windows XP booting from AV8's 8327-attached two SATA Western Digital Raptor disks, setup as striped;
- LSI Logic 2-channel SCSI card (with all other hard disks on it), namely: 2 x 73GB + 36GB on channel 0, 3 x 73GB striped (RAID 1) on channel 1. I am dedicating the 36GB SCSI disk on channel 0 as the Ubuntu boot volume.
- Normal complement of USB ports, firewire, Aopen modem, GB Ethernet controller, etc.
- 19" LCD monitor attached via ATI Radeon dual-screen VGA adapter.

My intention is to create the Ubunto residence/boot on the 36GB SCSI disk on SCSI channel 0 (LSI Logic PCI Controller), leaving the two WD SATA RAID disks intact for Windows XP boot.  I would need a dual-boot environment.  I'm not concerned with accessing the Windows NTFS disks from Ubunto if my hardware prevents this; otherwise, it would be nice, not a necessity.

I found bug 1334, which has the same problem description as the problem I'm having.  Theoretically, it was fixed in Breezy, but I couldn't find any details of what fix was.  I also read in the forum of someone who had parititioner@41% "hang" in Breezy who didn't have the problem when installing 5.04 first. I downloaded and tried installating 5.04, but same exact sympton occurs during 5.04 install, so I gave up that idea.

Based on all things I've read in the bug reports and forums, it's probably the 8237 SATA Raid controller on the MB with its two attached (striped) WD 36GB Raptor drives that is causing the hang. Perhaps a bug in the driver for the VIA SATA RAID controller ( 8237 ) is not supported yet. So, as of now, I still can't install either 5.04 or 5.10.

I tried physically disconnecting the two SATA disks, but this made no difference.  There is no facility in the BIOS to disable the SATA RAID controller (8237), so this is not an option (it also would mean that I couldn't use dual-boot, which is a mandatory requirement for my installation).

So I'm stuck.  Others have said that the 'hang' in the partitioner occurs in loading 'sd_mod', but I don't know how to ascertain this.  My bug report, #20735, has screen shots of a 'ps -ef' done when the 'hang' occurs (CTRL-ALT-F2 to console, then using digital camera to record screen output when 'ps -ef' was done).  However, I'm unable to interpret what this means.

I've searched for some method to have Ubunto avoid checking/testing/interrogating the two 8237-attached SATA RAID disks during the installation, but I've not yet found any method.  I'm sure someone more knowledgable of Ubuntu installation would know how/when I can "stop" the installation, disable the disks, and "resume" the installation.  If so, please let me know!

If anyone can offer any advice, please feel free!

Thanks, Tom

---

