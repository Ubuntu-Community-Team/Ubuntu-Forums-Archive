---
title: "CD drive won't work right"
date: 2009-06-15
forum: General Help
---

### Post by xaenyx on 2009-06-15
Edit: the problem was a short in the ide cable.  It would only work when twisted 'right', and problem was fixed with new cable.

So, I have this DVD-RAM/RW/CD-RW/etc drive.  I know that it works, because I used it to boot the cd that I installed ubuntu from.  In fact, it works just fine when reading installation/boot cds.

But, now that I have ubuntu installed, there is a problem.  When I put disks in, it will /start/ to read them (it will grab the directory structure and everything), but it then just sort of poops out on me, and won't let me read any files.  Sometimes it will start reading files (and will start creating thumbnails in the case of picture cds), but then it stops reading, thumbnails are incomplete, and I get IO errors when I try and open a file.  

Any idea what could be going on?  The CD drive is slave and the hard drive is master (verified in BIOS and also according to my jumper pins/the cable).

/var/log/messages is full of pages of this:
> 
Jun 15 18:19:09 alex-desktop kernel: [ 2685.400856] sr 6:0:1:0: [sr0] Sense Key : Hardware Error [current]
Jun 15 18:19:09 alex-desktop kernel: [ 2685.400865] sr 6:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Jun 15 18:19:11 alex-desktop kernel: [ 2687.537721] sr 6:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jun 15 18:19:11 alex-desktop kernel: [ 2687.537731] sr 6:0:1:0: [sr0] Sense Key : Hardware Error [current]
Jun 15 18:19:11 alex-desktop kernel: [ 2687.537740] sr 6:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)


---

### Post by mc4man on 2009-06-15
To eliminate a few things run this to ck. on the udma mode that's being used (udma2 or higher is good, 

```
sudo hdparm -i /dev/scd[COLOR="Red"]0[/COLOR]
```

(red assumes the drive is /dev/scd0, if not try scd1, current mode(s) will have *

also
```
grep "UDMA" /var/log/dmesg
```

a line like this can **usually** be ignored (blue

> [   21.151515] ata1.00: ATAPI: ATAPI   DVD A  DH20A4P, 9P59, max UDMA/66
[   21.151530] ata1.00: [COLOR="Blue"]limited to UDMA/33 due to 40-wire cable
[/COLOR]

a line saying 'soft reset' or similar is an issue

---

