---
title: "Does not resume from sleep"
date: 2009-02-15
forum: General Help
---

### Post by AcIDx0 on 2009-02-15
Hello,

My desktop system running Ubuntu 8.10 does not resume from sleep.
It briefly displays 2 lines of text I could not read, and then the screen is blank and the system is non responsive.

I have searched the forum and tried several things, but to no avail.

Please help.

System info and what I tried:

System has NVIDIA graphics card. Uses proprietary drivers.
Compiz is on.

I tried switching to other prop. driver, and to nv driver, and not using any driver at all. I also tried to shut down compiz.

---

### Post by AcIDx0 on 2009-02-16
*Bump 1/3* 

Anyone?

Nothing I found on the forums works. Anyone cares to help? At least point where to look?

---

### Post by geirha on 2009-02-16
I don't know much about how suspending works, but looking through log-files might reveal some clues. Attempt a suspend and resume, run «date» first and note down the time. Start the machine again, and then look at the following files

/var/log/Xorg.0.log.old
/var/log/syslog
/var/log/kern.log
/var/log/daemon.log

Specifically at the messages right after the time you noted down. Any error messages?

---

### Post by AcIDx0 on 2009-02-16
I did as you suggested. None of the files had entries for the noted time, except the daemon.log. The latter had entries about the bringing up the Ethernet interface with success and nothing more.

Ideas?

---

### Post by geirha on 2009-02-16
Hm. After resuming, have you tried looking at all the graphical consoles by hitting Ctrl+Alt+F7, Ctrl+Alt+F8, ..., Ctrl+Alt+F12?

---

### Post by AcIDx0 on 2009-02-16
OK, I managed to ssh to the system after resume. I examined the dmesg, and found something I guess is the cause...

```

[  137.000381] ACPI: Waking up from system sleep state S3

<skipped lines>

[  137.677422] ACPI Exception (exoparg2-0444): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFF) is beyond end of object [20080609]
[  137.677433] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.IDEC.IDE0._STM] (Node f7415918), AE_AML_PACKAGE_LIMIT
[  137.677471] ata1: ACPI set timing mode failed (status=0x300d)
[  137.678319] ACPI Exception (exoparg2-0444): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFF) is beyond end of object [20080609]
[  137.678329] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.IDEC.IDE1._STM] (Node f7415a08), AE_AML_PACKAGE_LIMIT
[  137.678362] ata2: ACPI set timing mode failed (status=0x300d)
[  137.687305] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[  137.709018] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[  137.733017] ohci_hcd 0000:00:03.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[  137.773014] ehci_hcd 0000:00:03.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23

< Skipped lines>

[  137.840291] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[  137.840295] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out


```

My knowledge stops here. :(  Any gurus to tell me why does the system hang?

geirha: no, that does not work....

---

### Post by geirha on 2009-02-16
From a short google on that ACPI error, it seems it may be a problem with certain ata drivers. Do you have any storage devices like flash cards connected? or just regular harddrives?

EDIT: At any rate, those error messages should not appear, so it's a bug in the kernel that should be reported. If you report it, it may take a while before it gets fixed and appear in a kernel update on ubuntu, but the developers might be able to give you a workaround or something.

[https://bugs.launchpad.net/ubuntu/+source/linux](https://bugs.launchpad.net/ubuntu/+source/linux)

---

### Post by AcIDx0 on 2009-02-17
This happens every time, no matter what storage device I try disconnecting. (did not try to disconnect the cd drive tho...)

I will file a bug with all info.

Isn't there a workaround? (I am asking this before googling, but still ;))

---

### Post by Lykopis on 2009-10-10
Yes the ACPI timing error seems to involve some ata drivers, but also has something to do with the way the 80 pin/conductor drive cable is detected. I have a PC that has an 80 pin on the primary and a 40 pin on the secondary. The error only shows on the primary where the 80 pin is, not the  secondary where the 40 pin is at. I was able to remove the error by using a add in card, something like an old promise 100/133. It's worth a try if you have one lying around.

---

### Post by leeza on 2009-10-10
hi, guys, ho to make a new post????????

---

