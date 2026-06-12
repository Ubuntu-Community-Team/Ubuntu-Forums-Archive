---
title: "Crash after Wine install"
date: 2008-12-08
forum: General Help
---

### Post by Russell Bliss on 2008-12-08
I just completed a synaptic wine install in intrepid and shortly after my computer froze entirely (I don't know if wine had anything to do with the crash I just thought I would include the relevant details).  I cannot reboot back to Ubuntu and on reboot I get:
...
chown:invalid group: 'syslog:adm'
chown:invalid group: 'syslog:adm'

*Doing Wacom setup...
*Starting kernel log daemon...
chown: invalid group: 'klog:klog'
/etc/rc2.d/S11klogd: 66: mkfifo: not found
chown: invalid group: 'klog:klog'
fail
chown: invalid group: 'messagebus'

then the screen goes to the message

"The GDM group 'gdm' does not exist. Please correct GDM configuration and restart GDM"

Upon booting in recovery mode and doing a disk check I get:

254.792236 ata6.00: exception Emask 0x10 SAct 0x0 SErr 0x3950000 action 0xe frozen
254.792298 ata6: SErr: { PHYRdyChg CommWake Dispar LinkSeq TrStaTrns UnrecFIS }
254.792358 ata6.00 cmd c8/00:18:87:bc:5f/00:00:00:00:00/ec tag 0 dma 12288in
254.792359 res d0/00:18:87:bc:5f/00:00:00:00:00/ec Emask 0x12 (ATA bus error)
254.792470 ata6.00: status: (busy)en
378.609196 ata6.00: exception mask 0x10 SAct 0x0 SErr 0x1910000 action0xefroz
378.609258 ata6: SError: { PHYRdyChg Dispar LinkSeq TrStatrns }
378.609309 ata6.00: cmd 25/00:40:4f:00:70/00:00:20:00:00/e0 tag 0 dma 32768in
378.609310 res d0/00:40:4f:00:70/00:00:20:00:00/e0 Emask 0x12 (ATA bus error)
378.609421 ata6.00: status: {busy}
/dev/sda1: |====================                                    | 
39.7%

and then it will not move any further.

What am I to do?
-Thanks,
Big Russ Bliss

---

