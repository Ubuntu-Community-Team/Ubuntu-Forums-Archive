---
title: "How do I access my Card Reader?"
date: 2005-08-04
forum: Desktop Environments
---

### Post by bittner on 2005-08-04
I have installed Kubuntu on my Toshiba Satellite M30X-167 notebook and I was amazed how good the system works. There are a few things, however, that seem not to work right away:

- The notebook has a built-in card reader (6-in-1) for SD, MMC, etc. which I do not succeed to access.

- Very much the same, the card reader unit on my EPSON Stylus Photo RX500 (which is a combined printer/scanner/cardreader device): I have no idea how to access it. (The printer though works fine, and I am optimistic to get scanning working.)

I was running SuSE 9.2 on my desktop machine before (which crashed recently and I had to buy the notebook) and there it was very easy with KDE to find the printer's card reader unit using Konqueror. (I recall it must have been something like media:// or devices:// or so.)

lsusb on the Konsole shows all information about the printer/scanner/cardreader, but the integration into Konqueror lacks, so I guess this must be a Kubuntu issue.

lspci seems to list some info about the internal card reader, but I might err.

Does anyone know how to get this working?
Peter

---

### Post by lol on 2005-08-04
I access mine the old fashioned way: I added an entry in my fstab, and I mount it manually.

The main problem is to find which device to use. For this, you can install the hal-device-manager, it should help you to find how to access your card reader.

For mine, depending on which kind of card I want to read, I have to use /dev/sda, sdb, sdc or sdd.

My fstab entry looks like this:
/dev/sda1       /mnt/flash      vfat    noauto,user     0       0

---

### Post by bittner on 2005-08-04
Okay, that's cool. I'm going to try it.

But still, I will probably need a Konqueror-integrated solution, because my wife uses the notebook and I don't want to make her fuzz around when something somehow does not work as expected.

It was very, very convenient the way it is realized in SuSE Linux, she liked the way it worked and she wants it back that way!   :-|  I'll try with a desktop shortcut for now (to mount and umount the device).

If anyone knows how to realize an automated, autodetect-like solution please let me know!

Cheers, Peter

---

### Post by Sav on 2005-08-05
If it is a Richo's card-reader there is no way.

---

### Post by jamesrw on 2005-08-09
I just ordered a compaq v2000z and realized the card reader will take some extra configuring to work. I found a couple links on another forum. This is for a winbond card reader.

[http://members.inode.at/g.schild/DIV/Winbond-howto.html](http://members.inode.at/g.schild/DIV/Winbond-howto.html)
[http://projects.drzeus.cx/wbsd/](http://projects.drzeus.cx/wbsd/)

I hope my notebook arrives soon so I can go through hell with the rest of you struggling.... or not, but we'll see.

---

### Post by James Wilford on 2005-08-09
Hi bittner,

I have a desktop PC at work which has a built-in card reader. Unfortunately, from what I could discover, it has no Linux support at all. If your lspci output includes the following lines:

0000:02:0c.0 CardBus bridge: ENE Technology Inc CB710 Cardbus Controller (rev 02)
0000:02:0c.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller

... then you're probably out of luck, unless anyone else knows better.

As for the reader in your printer, do a "tail -f /var/log/messages" while inserting a card, and see if something like the following comes up:

Aug 10 00:11:30 localhost kernel: SCSI device sdd: 504320 512-byte hdwr sectors (258 MB)
Aug 10 00:11:30 localhost kernel: sdd: Write Protect is off
Aug 10 00:11:30 localhost kernel: SCSI device sdd: 504320 512-byte hdwr sectors (258 MB)
Aug 10 00:11:30 localhost kernel: sdd: Write Protect is off
Aug 10 00:11:30 localhost kernel:  /dev/scsi/host3/bus0/target0/lun2: p1

This is on my home machine where I have a USB card reader. Then you might need to add a line to /etc/fstab like this:

/dev/sdd1       /media/sdcard   auto    rw,user,noauto  0       0

Obviously your device name might differ.

Good luck!

James

---

### Post by jamesrw on 2005-08-22
my lspci output (presario v2000z amd64):

0000:05:09.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:05:09.4 0805: Texas Instruments: Unknown device 8034

looks like a card reader but a dead end.

---

### Post by sweRascal on 2006-02-02
My laptop (HP nc4200) also shows the same thing...

0000:02:06.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:02:06.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033

I would sure appreciate any help in getting this to work.
Thanks in advance.

/A

---

### Post by nocturn on 2006-02-02
[QUOTE=sweRascal]My laptop (HP nc4200) also shows the same thing...

0000:02:06.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:02:06.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033

I would sure appreciate any help in getting this to work.
Thanks in advance.

/A[/QUOTE]

They're working on it, but it will probably be after kernel 2.6.15...

---

### Post by pakux on 2006-02-09
another candidate: Gateway MX3560....

(for both the internal card reader and the firewire port)

[FONT="Courier New"]0000:02:07.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:02:07.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:02:07.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033[/FONT]

we'll be wating !

---

### Post by jamesrw on 2006-02-10
there is a development in progress..

[http://tifm21.berlios.de](http://tifm21.berlios.de)

---

### Post by Marco Bresciani on 2006-02-25
I had Ubuntu Breezy and an Epson Stylus Photo RX500... but had no problem at all. Inserting a flash card inside the reader, the card is automounted. Running XSANE, the scanner works. Printer works too without problem.

---

### Post by Alegrya on 2006-03-18
I've got a Dell Inspiron 630m and thus far haven't had any luck with getting my card reader to work. I'm a little disconcerted about the general lack of success that people have written about. 

I'm running Ubuntu Breezy Badger 5.10.

---

### Post by Zaskoda on 2006-04-21
I have the 630m as well... I've read around and have yet to find anyone with a working card reader on the 630m.

Ubuntu is almost good on the 630m. The broke stuff includes:
 - card reader (obviously)
 - wireless (operational, but flakey on WEP... green led indicator doesn't work)
 - 1/2 of the multimedia keys work, other half don't
 - modem
 - native widescreen resolution (hack available)
 - sound issues (bad or no mixing, VLC crackles, headphones don't disable main output)
 - sleep mode locks up

Those are the main problems I've had... The lack of a card reader is going to run me off soon. The wifi issues already had me on the fence.

---

### Post by Zaskoda on 2006-04-21
Again, sorry for the double post (second one today), but this will be inspiring to other 630m owners..

Take from: [http://lokorn.neuf.fr/index.html](http://lokorn.neuf.fr/index.html)

"It seems that since I've been updated my laptop to Dapper Drake (unstable, though), the major issues have been solved (Sound and Card reader)"

Oh happy joy :D

---

