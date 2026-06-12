---
title: "Trouble mounting usb key on Hardy"
date: 2008-05-25
forum: Desktop Environments
---

### Post by sistoviejo on 2008-05-25
When I insert a usb drive it doesn't even appear on /dev.
Only way to mount it in Hardy is having it plugged in and then rebooting.
It appears to mount ok in other Hardy computers without need to reboot.
Any help appreciated.

---

### Post by ghantoos on 2008-05-25
Can you see it when doing:
```
sudo fdisk -l
```If you do, than just do:
```
sudo mount /dev/blaX /mnt/bla
```Cheers,

---

### Post by sistoviejo on 2008-05-25
> **ghantoos said:**
> Can you see it when doing:
```
sudo fdisk -l
```
Thanks but no, it doesn't show up.

---

### Post by ghantoos on 2008-05-25
What do you see in /var/log/messages when pluging your USB key?

---

### Post by sistoviejo on 2008-05-25
> **ghantoos said:**
> What do you see in /var/log/messages when pluging your USB key?

Nothing is written on /var/log/messages when I plug it in.

---

### Post by ghantoos on 2008-05-25
You should see something like this:
```

May 26 02:20:08 your_hostname kernel: [92342.957652] usb 5-5.2: new high speed USB device using ehci_hcd and address 9
May 26 02:20:08 your_hostname kernel: [92343.055118] usb 5-5.2: configuration #1 chosen from 1 choice
May 26 02:20:08 your_hostname kernel: [92343.055592] scsi8 : SCSI emulation for USB Mass Storage devices

```It looks like your PC does not handle your USB slot at all. bump.

---

### Post by sistoviejo on 2008-05-25
> **ghantoos said:**
> You should see something like this:
```

May 26 02:20:08 your_hostname kernel: [92342.957652] usb 5-5.2: new high speed USB device using ehci_hcd and address 9
May 26 02:20:08 your_hostname kernel: [92343.055118] usb 5-5.2: configuration #1 chosen from 1 choice
May 26 02:20:08 your_hostname kernel: [92343.055592] scsi8 : SCSI emulation for USB Mass Storage devices

```It looks like your PC does not handle your USB slot at all. bump.

I tried rebooting the computer with the usb key plugged in now, and the drive was mounted.
Then I umounted and unplugged it and plug it back in. It was mounted successfully. 
For some reason it's working fine now. It wants me to look like I'm crazy. :lolflag:
It'll probably start to fail after some more uptime. I'll post again if it happens.
Here's what appeared in /var/log/messages (I was using two different usb drives, an Ipod and a standard usb key):
```

May 25 22:38:15 silvio-laptop kernel: [  217.064674] usb 2-8: USB disconnect, address 4
May 25 22:38:20 silvio-laptop kernel: [  219.460596] usb 1-5: USB disconnect, address 2
May 25 22:38:31 silvio-laptop kernel: [  224.947377] usb 2-8: new high speed USB device using ehci_hcd and address 7
May 25 22:38:32 silvio-laptop kernel: [  225.105305] usb 2-8: configuration #1 chosen from 2 choices
May 25 22:38:32 silvio-laptop kernel: [  225.110283] scsi6 : SCSI emulation for USB Mass Storage devices
May 25 22:38:37 silvio-laptop kernel: [  228.399452] scsi 6:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
May 25 22:38:37 silvio-laptop kernel: [  228.409797] sd 6:0:0:0: [sdb] 19488471 4096-byte hardware sectors (79825 MB)
May 25 22:38:37 silvio-laptop kernel: [  228.411076] sd 6:0:0:0: [sdb] Write Protect is off
May 25 22:38:37 silvio-laptop kernel: [  228.414671] sd 6:0:0:0: [sdb] 19488471 4096-byte hardware sectors (79825 MB)
May 25 22:38:37 silvio-laptop kernel: [  228.415944] sd 6:0:0:0: [sdb] Write Protect is off
May 25 22:38:37 silvio-laptop kernel: [  228.415957]  sdb: sdb1
May 25 22:38:37 silvio-laptop kernel: [  228.427977] sd 6:0:0:0: [sdb] Attached SCSI removable disk
May 25 22:38:37 silvio-laptop kernel: [  228.428021] sd 6:0:0:0: Attached scsi generic sg2 type 0
May 25 22:39:02 silvio-laptop kernel: [  244.067768] usb 1-5: new full speed USB device using ohci_hcd and address 3
May 25 22:39:02 silvio-laptop kernel: [  244.165592] usb 1-5: configuration #1 chosen from 1 choice
May 25 22:39:02 silvio-laptop kernel: [  244.168497] scsi7 : SCSI emulation for USB Mass Storage devices
May 25 22:39:07 silvio-laptop kernel: [  246.767390] scsi 7:0:0:0: Direct-Access     Softick  Card Export      0001 PQ: 0 ANSI: 0 CCS
May 25 22:39:07 silvio-laptop kernel: [  246.797167] sd 7:0:0:0: [sdc] 3910656 512-byte hardware sectors (2002 MB)
May 25 22:39:07 silvio-laptop kernel: [  246.805149] sd 7:0:0:0: [sdc] Write Protect is off
May 25 22:39:07 silvio-laptop kernel: [  246.823443] sd 7:0:0:0: [sdc] 3910656 512-byte hardware sectors (2002 MB)
May 25 22:39:07 silvio-laptop kernel: [  246.836875] sd 7:0:0:0: [sdc] Write Protect is off
May 25 22:39:07 silvio-laptop kernel: [  246.836891]  sdc: sdc1
May 25 22:39:07 silvio-laptop kernel: [  246.843880] sd 7:0:0:0: [sdc] Attached SCSI removable disk
May 25 22:39:07 silvio-laptop kernel: [  246.843936] sd 7:0:0:0: Attached scsi generic sg3 type 0

```

---

### Post by sistoviejo on 2008-05-25
I waited a while and plugged the ipod back in and this is what showed up in /var/log/messages:

```

May 25 22:53:41 silvio-laptop kernel: [  713.551739] Pid: 0, comm: swapper Tainted: P        2.6.24-16-generic #1
May 25 22:53:41 silvio-laptop kernel: [  713.551741] 
May 25 22:53:41 silvio-laptop kernel: [  713.551742] Call Trace:
May 25 22:53:41 silvio-laptop kernel: [  713.551744]  <IRQ>  [__report_bad_irq+0x1e/0x80] __report_bad_irq+0x1e/0x80
May 25 22:53:41 silvio-laptop kernel: [  713.551775]  [note_interrupt+0x2ad/0x2e0] note_interrupt+0x2ad/0x2e0
May 25 22:53:41 silvio-laptop kernel: [  713.551785]  [handle_level_irq+0xb3/0x120] handle_level_irq+0xb3/0x120
May 25 22:53:41 silvio-laptop kernel: [  713.551793]  [do_IRQ+0x7b/0x100] do_IRQ+0x7b/0x100
May 25 22:53:41 silvio-laptop kernel: [  713.551796]  [default_idle+0x0/0x40] default_idle+0x0/0x40
May 25 22:53:41 silvio-laptop kernel: [  713.551799]  [default_idle+0x0/0x40] default_idle+0x0/0x40
May 25 22:53:41 silvio-laptop kernel: [  713.551802]  [ret_from_intr+0x0/0x0a] ret_from_intr+0x0/0xa
May 25 22:53:41 silvio-laptop kernel: [  713.551805]  <EOI>  [default_idle+0x29/0x40] default_idle+0x29/0x40
May 25 22:53:41 silvio-laptop kernel: [  713.551821]  [cpu_idle+0x6f/0xc0] cpu_idle+0x6f/0xc0
May 25 22:53:41 silvio-laptop kernel: [  713.551843] 

```

It wasn't mounted and it didn't appear in /dev/sdb

If I unplug it and plug it back in, nothing shows up in /var/log/messages now

---

### Post by sistoviejo on 2008-05-31
anyone?

update: Found out what it was...
I had put noapic and nolapic in the kernel parameters in /boot/grub/menu.lst.
Had done this to get suspend to work.
Seems that these changes make usb keys not to work very nicely on my system.
Guess I'll have to choose between being able to suspend or being able to use USB keys.
Hppy to be able to find out what it was though! :)

---

