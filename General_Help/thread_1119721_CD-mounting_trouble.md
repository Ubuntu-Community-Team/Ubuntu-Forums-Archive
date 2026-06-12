---
title: "CD-mounting trouble"
date: 2009-04-08
forum: General Help
---

### Post by luotinen on 2009-04-08
Hi!

I haven't been mounting CDs in a while and now I'm happy to notice that mounting CDs automatically is broken (probably due to some update)

So. Instead of seeing all the files on my CD I get this crap:
[I]Cannot mount Gnomebaker disc
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.[/I]

And it actually is mean enough not to mount it. So I have to mount it from the shell:
[B]sudo umount /dev/scd0
sudo mount -t iso9660 /dev/scd0 /media/cdrom[/B]

And then it works perfectly.

So how can I fix it to mount automatically again?

I'm running Intrepid Ibex with all repos and all latest updates. My drive is PATA (IDE) Samsung:
[I]pata_amd
        *-cdrom
             description: DVD-RAM writer
             product: CD/DVDW SH-S182D
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             logical name: /media/cdrom0
             version: SB00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /media/cdrom0
                configuration: mount.fstype=iso9660 mount.options=ro state=mounted[/I]

---

### Post by FrankT-Qc on 2009-04-08
I would start by ditching GnomeBaker... not the best thing out there and it does make things unstable. 

Have a look at brasero or k3b, they both do pretty much the same (better) job and don't mess with FUSE or Nautilus (read : wont mess with automounting)

have fun

---

### Post by luotinen on 2009-04-08
[B]sudo apt-get remove gnomebaker
sudo apt-get install k3b[/B]

Immediate effect: mounting does not work and the GnomeBaker error message remains (convinient considering I don't have it installed anymore...)
After X reboot: mounting does not work and the GnomeBaker error remains
After reboot: mounting does not work and GnomeBaker error remains

So ditching GnomeBaker had no effect whatsoever. It did not even remove the error message.
[B]
/var/log/messages[/B] is flooded with:
[I]Apr  8 17:24:39 tamergol kernel: [  400.419014] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr  8 17:24:39 tamergol kernel: [  400.419027] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Apr  8 17:24:39 tamergol kernel: [  400.419037] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit[/I]

---

### Post by Yashiro on 2009-04-08
Are you mounting the CD in your /etc/fstab?
If you're using gnome automount you don't want to be mounting it in the fstab.

Additionally, did you at some point right click your CD drive and try to set its mount point in the gnome properties dialog pages?

---

