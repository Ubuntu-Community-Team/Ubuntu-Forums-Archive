---
title: "usb dvd drive intermittently available"
date: 2006-09-18
forum: Desktop Environments
---

### Post by backdoc on 2006-09-18
I have a Lite-On USB DVD burner that I'm having some trouble with.  It is being recognized by the system.  But, it is only intermittently available to applications.  For instance, I was able to play a DVD in it earlier tonight.  Now, I can't use it in k3b or GnomeBaker.

I know the system recognizes it right now because I see it in /proc/usb/devices, /var/log/messages/, in Gnome Device Manager and in proc/scsi/scsi.  Oddly Gnome Device Manager sees it as a "Lite-On".  But, the value in /proc/scsi/scsi is has weird values for the vendor.  For example,
[INDENT]
Host: scsi5 Channel: 00 Id: 00 Lun: 00
Vendor: 4&4&4&4& Model: 4&4&4&4&4&4H H H Rev:  H H
Type:   Unknown                          ANSI SCSI revision: 04
[/INDENT]

I'm not really sure how to go about troubleshooting this.  I don't see it attached to any devices, so I don't know how to attempt to mount it.  Any suggestions?

Here's a couple of relevant screenshots (if I got them attached properly).

---

### Post by backdoc on 2006-09-24
Problem solved.  For the benefit of others who may find this post via a search, I thought I would update my own post.

It seems that a firmware upgrade of my burner was required.

cat /proc/scsi/scsi now shows this:
[INDENT]
Host: scsi4 Channel: 00 Id: 00 Lun: 00
Vendor: LITE-ON  Model: DVDRW SOHW-1693S Rev: KS0B
Type:   CD-ROM                           ANSI SCSI revision: 02
[/INDENT]

---

