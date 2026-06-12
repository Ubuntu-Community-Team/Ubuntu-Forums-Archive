---
title: "issues with media drive"
date: 2009-02-09
forum: General Help
---

### Post by zetagirl on 2009-02-09
It tells me that

You are not privileged to mount the volume 'HP Personal Media Drive'.


What the french toast...??? Im not privileged...

---

### Post by HermanAB on 2009-02-09
Hmm, well, if you are an unprivileged common user, then you got to wield the secret weapon called 'sudo'.

Try this:
Plug device in
$ sudo dmesg
Find the device name

$ sudo mkdir /mnt/wherever
$ sudo mount /dev/whatever /mnt/wherever

Cheers,

Herman

---

### Post by zetagirl on 2009-02-09
Sorry  but im a complete noob  and i just made the switch from windoze....what do i put for wherever?

$ sudo mkdir /mnt/wherever
$ sudo mount /dev/whatever /mnt/wherever

when I typed in the sudo dmesg i got this

[  395.452817] scsi 4:0:0:0: Direct-Access     ST316002 3A               8.11 PQ: 0 ANSI: 0
[  395.465893] sd 4:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[  395.466759] sd 4:0:0:0: [sdb] Write Protect is off
[  395.466762] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  395.466765] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  395.467755] sd 4:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[  395.468633] sd 4:0:0:0: [sdb] Write Protect is off
[  395.468635] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  395.468637] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  395.468641]  sdb: sdb1 < sdb5 >
[  395.494880] sd 4:0:0:0: [sdb] Attached SCSI disk
[  395.494923] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 2593.320182] usb 5-5: USB disconnect, address 5
[ 1038.034624] usb 5-5: new high speed USB device using ehci_hcd and address 6
[ 2594.231607] usb 5-5: configuration #1 chosen from 1 choice
[ 1038.116018] scsi5 : SCSI emulation for USB Mass Storage devices
[ 1038.119350] usb-storage: device found at 6
[ 1038.119354] usb-storage: waiting for device to settle before scanning
[ 2595.818362] usb-storage: device scan complete
[ 2595.840630] scsi 5:0:0:0: Direct-Access     ST316002 3A               8.11 PQ: 0 ANSI: 0
[ 1038.753192] sd 5:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[ 1038.753997] sd 5:0:0:0: [sdb] Write Protect is off
[ 1038.754000] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1038.754003] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1038.754994] sd 5:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[ 1038.755871] sd 5:0:0:0: [sdb] Write Protect is off
[ 1038.755874] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1038.755876] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1038.755879]  sdb: sdb1 < sdb5 >
[ 1038.778698] sd 5:0:0:0: [sdb] Attached SCSI disk

---

### Post by zetagirl on 2009-02-09
bump...any one?

---

### Post by adult swim on 2009-02-09
try this from a terminal, Applications>accessories>terminal.
type in ```
sudo mount /dev/sdb1 /mnt
```  then hit enter, type in your password and hit enter again.  now go to places>home folder.  click on the filesystem which is in the left pane and then browse to /mnt.  your stuff should appear there.

---

### Post by zetagirl on 2009-02-09
Thank you!!!! I see it now!!!!!

---

