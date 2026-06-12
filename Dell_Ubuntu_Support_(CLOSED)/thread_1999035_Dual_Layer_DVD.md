---
title: "Dual Layer DVD"
date: 2012-06-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bala150985 on 2012-06-07
Hi

This is a model of DVD which I have,  I can play a single  layer DVD on it,  However when I try a Dual Layer DVD it is not working  :-(

I am running Lucid Lynx.  The Dual Layer DVD is not the problem as it plays on other system.

cat /proc/scsi/scsi 
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: HL-DT-ST Model: DVD+-RW GSA-T40N Rev: A100
  Type:   CD-ROM                           ANSI  SCSI revision: 05


I have also tried following this link [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

sudo apt-get install libdvdread4 and

/usr/share/doc/libdvdread4/install-css.sh 

Rebooted my PC still no effect.

---

