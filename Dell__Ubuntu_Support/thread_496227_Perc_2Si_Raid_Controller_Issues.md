---
title: "Perc 2/Si Raid Controller Issues"
date: 2007-07-08
forum: Dell  Ubuntu Support
---

### Post by MrBeanie on 2007-07-08
I orginally had issues trying to get Ubuntu Server to detect the Raid 2/Si controller on installation so I updated the System Bios and Raid Controller Bios etc etc to Dell's Latest. Then I was able to install to OS. Previously to that I had run Windows 2000 Server on it with no Hardware Issues. However since running the box for a couple of weeks I have noticed the following errors in dmesg:

755375.891339] AAC:SCSI Channel[0]: Timeout Detected On 1 Command(s)
[766165.685017] AAC:ID(0:00:0) Timeout detected on cmd[0x2a]
[766165.685992] AAC:SCSI Channel[0]: Timeout Detected On 1 Command(s)
[771802.934589] AAC:ID(0:02:0) Timeout detected on cmd[0x2a]
[771802.935538] AAC:SCSI Channel[0]: Timeout Detected On 1 Command(s)
[792103.374946] AAC:ID(0:04:0) Timeout detected on cmd[0x2a]
[792103.375955] AAC:SCSI Channel[0]: Timeout Detected On 1 Command(s)
[821317.492364] AAC:ID(0:03:0) Timeout detected on cmd[0x2a]
[821317.493321] AAC:SCSI Channel[0]: Timeout Detected On 1 Command(s)
[827910.908703] AAC:ID(0:00:0) Timeout detected on cmd[0x2a]
[827910.909730] AAC:SCSI Channel[0]: Timeout Detected On 1 Command(s)
[897750.248724] AAC:ID(0:03:0) Timeout detected on cmd[0x2a]
[897750.249676] AAC:SCSI Channel[0]: Timeout Detected On 1 Command(s)

Also, if I hammer the Disks subsytem by trying to do an apt-mirror the machine hangs
and on the console it looks like some weird kernel panic loop (sry I don't have an Output for this)
I expect that it is a aacraid driver issue not a hardware issue ,as the machine was fine on the previous OS.
Anyone have any clues on this one? Dodgy Dell Firmware maybe?

Cheers

---

### Post by sr20ve on 2007-07-09
What kind of a system is this in?

Do the HDDs seem to be responding in the raid controller bios?

Do you know what firmware was on the raid controller before you upgraded to the latest?

---

### Post by MrBeanie on 2007-07-10
Sadly I can't remember what Firmware Version was running before i upgraded but it was old enough that ubuntu wouldn't detect the raid controller at all. It is currently running on a Poweredge 2400. The Hard drives are responding enough that the system is currently running with low load. One thing I haven't done is attempt to upgrade the disk firmware, although Dell say this is optional. I have my doubts that this is the problem.

---

