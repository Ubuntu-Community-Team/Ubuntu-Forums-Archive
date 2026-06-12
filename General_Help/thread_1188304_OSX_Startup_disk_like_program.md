---
title: "OSX Startup disk like program"
date: 2009-06-15
forum: General Help
---

### Post by bacardiandwatermelon on 2009-06-15
Hi guys,
In OSX there is an option via a program called startup disk (or something) to choose what you want to boot from after the comp has restarted e.g. hdd, cd, flashdrive.. I was wondering if there was anything like this for ubuntu? Or whether it is just a mac thing.. Cheers

---

### Post by 311005901 on 2009-06-15
[rEFIt]("http://refit.sourceforge.net/") may be what you're looking for. :D

---

### Post by DGortze380 on 2009-06-15
> **bacardiandwatermelon said:**
> Hi guys,
In OSX there is an option via a program called startup disk (or something) to choose what you want to boot from after the comp has restarted e.g. hdd, cd, flashdrive.. I was wondering if there was anything like this for ubuntu? Or whether it is just a mac thing.. Cheers

On a PC, this is handled by the BIOS.

Press the specified key at boot to enter the BIOS, set your boot order there.

Mac takes a slightly different approach, thus the need to specify a start-up disc.

If you're running a Mac with an EFI Partition, rEFIt is a great option.

---

### Post by bacardiandwatermelon on 2009-06-15
Yeah I think you have answered my question, I have a pc not a mac, I wasn't sure how mac did its efi partition thing. I was working on a mac today and I thought it was a separate program doing the job. I liked the idea of switching what you want to boot, then walking away for a coffee then coming back to the comp and it has already booted for you.

---

### Post by synchro505 on 2009-06-15
Also on the Mac, if you have multiple drives which are bootable (internal or external) you can hold down the Option key after the chime and you will be prompted to choose which drive you'd like to boot from.

Or, if you want to only boot from a bootable DVD, hold down the C key after the chime and it will force the Mac to boot from the bootable DVD.

Sort of a BIOS for dummies!

---

### Post by DGortze380 on 2009-06-15
> **synchro505 said:**
> Also on the Mac, if you have multiple drives which are bootable (internal or external) you can hold down the Option key after the chime and you will be prompted to choose which drive you'd like to boot from.

Or, if you want to only boot from a bootable DVD, hold down the C key after the chime and it will force the Mac to boot from the bootable DVD.

Sort of a BIOS for dummies!

Not to get all defensive, not looking for a fight ... I hate it when people do that ... but Open Firmware and EFI are actually much more powerful and a simple BIOS Setup Screen...

---

### Post by synchro505 on 2009-06-15
So true. You are right. I stand corrected. :)

> **DGortze380 said:**
> Not to get all defensive, not looking for a fight ... I hate it when people do that ... but Open Firmware and EFI are actually much more powerful and a simple BIOS Setup Screen...

---

