---
title: "IS there a way to install an iso file without burning?"
date: 2010-03-27
forum: Gaming &amp; Leisure
---

### Post by gordong11 on 2010-03-27
I have a game that has 4 iso images, and I want to install it with wine. Can someone explain how to install without burning? I'm guessing you have to start by mounting the iso file....but I do not know how to do this.


Thanks

G ;)

---

### Post by gordong11 on 2010-03-27
mounted with acetoneiso from software center. sweet.

---

### Post by jacksaff on 2010-03-27
You can mount iso files using the following command. You need (an ideally empty) directory in which to mount it, but it can be anywhere.

sudo mount yourisofile.iso directoryinwhichtomountit -o loop

---

### Post by jflaker on 2010-03-27
you can mount an ISO like a hard disk....OR, if this is a bootable ISO, you can create a VirtualBox machine and boot have VBox mount the ISO for booting.


So, yes.

---

### Post by Austin25 on 2010-03-27
I was going to say unetbootin, but it's for a game.

---

### Post by gordong11 on 2010-03-27
> **jacksaff said:**
> You can mount iso files using the following command. You need (an ideally empty) directory in which to mount it, but it can be anywhere.

sudo mount yourisofile.iso directoryinwhichtomountit -o loop

Thanks, Sweet I knew there was a way in the console, rather than acetone. Thank you for the help.

---

