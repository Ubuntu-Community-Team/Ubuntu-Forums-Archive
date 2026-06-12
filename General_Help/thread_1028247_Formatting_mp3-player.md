---
title: "Formatting mp3-player"
date: 2009-01-02
forum: General Help
---

### Post by rang501 on 2009-01-02
I have a Acme V-500X player. It has 4GB memory.
Here's what I did:
I wanted to format my player, so I installed gparted. At first attempt to format my player Gparted notified something about label name issue (or similar, i haven't get this notification anymore). I don't exactly remember what I did to get rid of that message. Anyway, I got my player formatted to fat32. Then I copied one music file to player. I unmount my player. At players filemanager I see some folders and files but I copied only one file. Filenames are weird also (uncommon characters). Something is wrong.

So, I tried to format that player under Vista. Formatting takes a lot of time (something half an hour, gparted formatted it much faster). When done, I plugged it to my laptop (ubuntu 8.10) and nothing happens. It doesn't mount my player.

Gparted shows that player uses unknown filesystem. I formatted that drive again, using gparted but now with fat16. And that same thing happens again.

Both vista and ubuntu sees that copied file correctly.

Can anyone give me instructions how to format my player under ubuntu?

dmesg seems to be alright:

[354294.468121] usb 5-3: new high speed USB device using ehci_hcd and address 21
[354294.602883] usb 5-3: configuration #1 chosen from 1 choice
[354294.604369] scsi17 : SCSI emulation for USB Mass Storage devices
[354294.606585] usb-storage: device found at 21
[354294.606591] usb-storage: waiting for device to settle before scanning
[354299.604510] usb-storage: device scan complete
[354299.605124] scsi 17:0:0:0: Direct-Access     RockChip USB MP3          1.00 PQ: 0 ANSI: 0
[354299.605608] scsi 17:0:0:1: Direct-Access     RockChip USB  SD          1.00 PQ: 0 ANSI: 0 CCS
[354299.611895] sd 17:0:0:0: [sdb] 8013824 512-byte hardware sectors (4103 MB)
[354299.612461] sd 17:0:0:0: [sdb] Write Protect is off
[354299.612467] sd 17:0:0:0: [sdb] Mode Sense: 03 00 00 00
[354299.612472] sd 17:0:0:0: [sdb] Assuming drive cache: write through
[354299.615082] sd 17:0:0:0: [sdb] 8013824 512-byte hardware sectors (4103 MB)
[354299.615715] sd 17:0:0:0: [sdb] Write Protect is off
[354299.615721] sd 17:0:0:0: [sdb] Mode Sense: 03 00 00 00
[354299.615725] sd 17:0:0:0: [sdb] Assuming drive cache: write through
[354299.615734]  sdb: sdb1
[354299.622745] sd 17:0:0:0: [sdb] Attached SCSI removable disk
[354299.622981] sd 17:0:0:0: Attached scsi generic sg2 type 0
[354299.624428] sd 17:0:0:1: [sdc] Attached SCSI removable disk
[354299.624562] sd 17:0:0:1: Attached scsi generic sg3 type 0

---

### Post by timcredible on 2009-01-02
umm... why did you format your mp3 player?  

anyway, if i were you, i'd see if there's an option in the mp3 player itself for formatting or erasing the drive, and do that to get it back to the original settings.  if that's not available, you need to find out what filesystem the mp3 player can read and format to that - i would guess fat32, but who knows.  it may also need a certain directory structure.

also, when plugging it in, if ubuntu doesn't know what it is, it doesn't do anything with it by default, you may have to mount it manually via places->computer

---

### Post by bradthewanderer on 2009-01-02
Certain mp3 players just don't work no matter what I have ever done with them. Good luck.

---

### Post by hyperdude111 on 2009-01-02
when you go to your player does it work?

If not you have killed it. The firmware is often kept in the main player partition if you format you may have killed it. I did this to a phillips mp3 and an ipod. (I know i never learn:))

If you want to clear all the space just mount it in ubuntu and delete all the folders. They will then go to the .trash-1000 folder on the root of the mp3 just delete that folder. 

Hopefully it still works

---

### Post by rang501 on 2009-01-04
Firmware should not be a problem because I can install firmware (I have firmware on cd). I tried also installing firmware again, under vista and formatted it to fat32. I copied some files to player but I cant see any files there (players file manager) but on both computers I can see them (vista/ubuntu).

I'll try to format player again with gparted.

Does MBR can cause problems?

---

