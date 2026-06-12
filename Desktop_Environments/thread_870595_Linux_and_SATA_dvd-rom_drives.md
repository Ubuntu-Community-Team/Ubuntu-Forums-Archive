---
title: "Linux and SATA dvd-rom drives"
date: 2008-07-26
forum: Desktop Environments
---

### Post by uknowho008 on 2008-07-26
I just put together a new computer and I was surprised to find that windows installed with no problems and ubuntu gets hung up because it doesn't seem to support SATA dvd-rom drives. Is there a quick way to get around this? And is this being worked on? It seems like it wouldn't be too difficult to support SATA drives and and a fairly important thing to have working. Thanks

---

### Post by bhankins on 2008-07-26
It does support sata dvd drives can you post an error message or something?

here is mine:
```
[    32.196881] Driver 'sr' needs updating - please use bus_type methods
[   32.271012] sr0: scsi3-mmc drive: 1x/48x writer cd/rw xa/form2 cdda tray
[   32.271017] Uniform CD-ROM driver Revision: 3.20
[   32.271056] sr 6:0:0:0: Attached scsi CD-ROM sr0
[   32.274438] sr1: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
[   32.274465] sr 6:0:1:0: Attached scsi CD-ROM sr1
```

---

### Post by uknowho008 on 2008-07-26
It was a few days ago. I just remember it couldn't mount the disk for the installation. I boot off the disk and get  passed the language select and press enter where it has the installation option then it starts its thing and then it loops the disk mounting error. I'll pop the disk in again so i can be a little more specific.

---

### Post by uknowho008 on 2008-07-26
I actually just booted the intrepid alpha disk and it worked just fine...

Maybe I'll just install that??

---

### Post by uknowho008 on 2008-07-29
Well I'm having problems with intrepid, so now back to Hardy.

Here is the error I'm getting when I try to boot the hardy disk.

```

buffer I/O error on devise fd0, logical block 0
ata4.00: revalidation failed (errno=-5)
ata6.00 status: {DRDY}

```

Thanks guys.

---

### Post by drifter129 on 2008-07-29
the 1st part of the message - "buffer I/O error on devise fd0, logical block 0" - relates to your floppy drive. if you don't have a floppy drive installed, try disabling it within the BIOS and give it another try.

---

### Post by uknowho008 on 2008-07-29
> **drifter129 said:**
> the 1st part of the message - "buffer I/O error on devise fd0, logical block 0" - relates to your floppy drive. if you don't have a floppy drive installed, try disabling it within the BIOS and give it another try.

I think it's disabled but I'll take a look.

---

### Post by uknowho008 on 2008-07-29
Ok, i disabled the floppy. Now I get this.

```

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in Shell Cash)

Enter 'help' for a list of built-in commands

(initreamfs)

```

And then if you wait a minute I start getting this error again.

> ata5.00: revalidation failed (errno=-5)

---

### Post by uknowho008 on 2008-07-29
Any ideas?

I'd rather not have to stick with windows on my new pc.

---

### Post by drifter129 on 2008-07-30
i would be interested to see if you have either an optical or hard drive connected to ata5..
if you are trying to install ubuntu, try pressing F6 on the initial menu screen and adding this to the end of the boot options "irqpoll all_generic_ide".
(obviously without quotations...)

---

### Post by pietjanjaap on 2008-07-30
Chech your bios settings.
sata settings, there are a few possibilities, try them. like sata to ide or something like that.

---

### Post by uknowho008 on 2008-07-30
> **drifter129 said:**
> i would be interested to see if you have either an optical or hard drive connected to ata5..
if you are trying to install ubuntu, try pressing F6 on the initial menu screen and adding this to the end of the boot options "irqpoll all_generic_ide".
(obviously without quotations...)

I actually dont have anything connected to ata5. My two hard drives are on 1 and 2 and my dvd drive is on 6. I will give that boot option a shot.

---

### Post by uknowho008 on 2008-07-30
"irqpoll all_generic_ide" worked. I'll attempt to install it later when I get off work. Thanks for all the help.

For the record switching the SATA settings caused the ubuntu disk to not boot at all. It went straight to windows.

---

### Post by drifter129 on 2008-07-30
good stuff, glad its is now working for you..

---

