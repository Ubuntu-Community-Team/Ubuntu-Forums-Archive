---
title: "Compact flash card not recognized in card reader"
date: 2005-12-26
forum: General Help
---

### Post by gunslinger on 2005-12-26
Hi all,
I have a 6 in 1 card reader that I use to transfer photos from my compact flash (CF) card.
Problem is that when I insert the CF card, it is not picked up and therefore I cannot mount it. It only gets picked up when I reboot with the CF card in the reader and then  I can mount it.
The first time I plugged in the card reader, it recognized it fine, I have tried unplugging it, replugging it both with and without the CF card in but to no avail.
Nothing gets logged in /var/log/messages.
It is supposed to be /dev/sda[1] but when I go to mount it, it says "mount: special device /dev/sda1 does not exist"
The entry in fstab I have for it is
"/dev/sda1	/media/compactflash	vfat	rw,user,noauto	0	0"

I dont know if its relevant but its on a usb1.1 port, whenever I plug it into a usb2 port it continuously posts these messages in /var/log/messages

usb 5-3: new high speed USB device using ehci_hcd and address 38
usb 5-3: new high speed USB device using ehci_hcd and address 40
usb 5-3: new high speed USB device using ehci_hcd and address 42
usb 5-3: new high speed USB device using ehci_hcd and address 44
usb 5-3: new high speed USB device using ehci_hcd and address 46
....
I will add a separate thread about this. Done [here]("http://ubuntuforums.org/showthread.php?p=605461")

Any help would be great.

--
JB
Brown is the new black

---

### Post by AndyAWS on 2005-12-28
I have the same problem with the card reader on my HP-PSC printer. I have to insert the memory card then re-boot to get it to mount.

Quite annoying....

There must be something we're missing in the fstab entry but I haven't found an answer yet.

---

### Post by mflash on 2005-12-28
Hi all,

Having a similar problem with an internal card reader (USB 2.0): same symptoms,
just shows the following:

usb 2-6: new high speed USB device using ehci_hcd and address 4

Oddly enough, an **external** card reader (also on a USB 2.0 port), works 
perfectly - creates device nodes, mounts the volume, etc.

Maybe we need a special configuration parameter somewhere... I have no
clue where to look :(

---

### Post by gunslinger on 2005-12-29
As someone pointed out to me, it might not always be mounted in the same place, so one time it might be sda then sdb etc..
Try, 
dmesg | grep SCSI
after you put it in.
I havent tried this yet.

JB

---

### Post by mflash on 2006-01-02
[QUOTE=gunslinger]As someone pointed out to me, it might not always be mounted in the same place, so one time it might be sda then sdb etc..
Try, 
dmesg | grep SCSI
after you put it in.
I havent tried this yet.

JB[/QUOTE]

Thanks, but there seems to be something wrong with my internal reader, as
sometimes it doesn't show on dmesg (or on /var/log/messages) at all...

---

### Post by gunslinger on 2006-01-02
[QUOTE=mflash]Thanks, but there seems to be something wrong with my internal reader, as
sometimes it doesn't show on dmesg (or on /var/log/messages) at all...[/QUOTE]

Yeah, mine too :(

---

