---
title: "Problem on startup with libata_core.c"
date: 2006-08-11
forum: Desktop Environments
---

### Post by nikky on 2006-08-11
On Ubuntu startup i get the following message:

[17179589.512000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531

What is it?

I have a Toshiba Satellite M40X-269 and Ubuntu 6.06

The hardware of the notebook is here 
[http://it.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=IT&PRODUCT_ID=106340&DISC_MODEL=1](http://it.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=IT&PRODUCT_ID=106340&DISC_MODEL=1)

---

### Post by edthefox on 2006-08-18
I know this isn't the place for server support, but I get the same message on my screen.

I am in the process of setting up a samba server for my local network. It's gonna be headless so it's just setting there while I do all the configuration and and installation from across the room using putty on my xp workstation.
I just noticed these two messages on the terminal :

```
Ubuntu 6.06 LTS podrido tty1

podrido login: [4295749.016000] Assertion Failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
[4295749.026000] Assertion Failed! qc->n_elem > 0,drivers/scsi/libata-core.c,ata_fill_sg,line=2531
```

I know this message***=not good***, but to what degree?, can it be ignored?

methinks this may be an issue with my sata controller but it's an onboard intel so i figure it's pretty much industry standard and should work fine with no issues but I'm probably wrong.

I have some experience with redhat fedora and gentoo, but don't know anything about Ubuntu or Debian.

Any help would be appreciated!

---

