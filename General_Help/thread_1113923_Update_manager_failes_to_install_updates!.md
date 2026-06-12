---
title: "Update manager failes to install updates!"
date: 2009-04-02
forum: General Help
---

### Post by Goggeli on 2009-04-02
Hello! Need some help! My update manager fails to install new updates, it worked before, but now it won't install any updates! Iget this crash report:


[IMG]http://img12.imageshack.us/img12/2750/screenshotboj.png[/IMG] 

I also have a problem with my firefox, greying out and freezing for some time, and that happends alot, I have no idea why!

Thanks
Goggeli

EDIT: I also get this message from update manager: 

[IMG]http://img18.imageshack.us/img18/5841/screenshot1ckp.png[/IMG]

EDIT2: In English: ....failed in buffer_read(fd)

---

### Post by xenophed on 2009-04-02
sounds like a hard drive problem check /var/log/kernel.log for errors a.k.a. seek : read or something like that

---

### Post by Goggeli on 2009-04-02
Did what you said, and here is a clip out of the log-file: "...Mar 31 11:50:35 oye-laptop kernel: [ 3964.298584] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 31 11:50:35 oye-laptop kernel: [ 3964.299595] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Mar 31 11:50:35 oye-laptop kernel: [ 3964.300247] sd 2:0:0:0: [sda] Write Protect is off
Mar 31 11:50:35 oye-laptop kernel: [ 3964.300257] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 31 11:50:35 oye-laptop kernel: [ 3964.301695] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 31 12:20:15 oye-laptop kernel: [ 5744.867091] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Mar 31 12:20:15 oye-laptop kernel: [ 5744.867101] ata3.00: irq_stat 0x40000001
Mar 31 12:20:15 oye-laptop kernel: [ 5744.867109] ata3.00: cmd c8/00:08:25:27:eb/00:00:00:00:00/e6 tag 0 dma 4096 in
Mar 31 12:20:15 oye-laptop kernel: [ 5744.867111]          res 51/01:00:27:27:eb/00:00:06:00:00/e6 Emask 0x1 (device error)
Mar 31 12:20:15 oye-laptop kernel: [ 5744.867116] ata3.00: status: { DRDY ERR }
Mar 31 12:20:15 oye-laptop kernel: [ 5744.868505] ata3.00: configured for UDMA/100
Mar 31 12:20:15 oye-laptop kernel: [ 5744.868519] ata3: EH complete
Mar 31 12:20:19 oye-laptop kernel: [ 5748.750948] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Mar 31 12:20:19 oye-laptop kernel: [ 5748.750962] ata3.00: irq_stat 0x40000001
Mar 31 12:20:19 oye-laptop kernel: [ 5748.750975] ata3.00: cmd c8/00:08:25:27:eb/00:00:00:00:00/e6 tag 0 dma 4096 in
Mar 31 12:20:19 oye-laptop kernel: [ 5748.750978]          res 51/01:00:27:27:eb/00:00:06:00:00/e6 Emask 0x1 (device error)
Mar 31 12:20:19 oye-laptop kernel: [ 5748.750986] ata3.00: status: { DRDY ERR }
Mar 31 12:20:19 oye-laptop kernel: [ 5748.752434] ata3.00: configured for UDMA/100
Mar 31 12:20:19 oye-laptop kernel: [ 5748.752459] ata3: EH complete
Mar 31 12:20:23 oye-laptop kernel: [ 5752.633808] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0..."

Does this say anything about my problem? I want to add that my computer had problems booting ubuntu, but vista worked fine, I ran the ubuntu-check thing from boot, and after, it booted fine again:S Anyway thanks for all answers! And if there is a hard-drive problem, what can I do? Some time ago, I was just running vista, and it crashed(think it was hard-drive problem) and I formated it, installed ubuntu with a small partition for vista at the disk! I really hope I won't have to formate again, for it's just a month or so ago, since last time...:S

Goggeli

EDIT:
I want to add that I have installed programs, manually at it has worked just fine, it's just update manager who seams to be the problem, and the boot thin, but that's just happen once.

---

