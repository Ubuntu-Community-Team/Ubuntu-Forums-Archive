---
title: "Want to update the BIOS of my old P4 5100 Dell Dimension"
date: 2009-04-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Scubdup on 2009-04-16
My PC doesn't want to recognise more than 3.2 gb of my 5gbs of RAM. I put this down to a hoisting/mapping problem but my current BIOS doesn't appear to have any option to amend that. I figure my best bet is a BIOS update.

Found [these instructions]("http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&dl=false&l=en&s=gen&docid=3031F8260CCA927FE040A68F5B2833EF&doclang=en&cs=") on the Dell website but can't follow the download part. Instructions 3 to 6 make no sense to this novice.

How can I run the commands at the command line ansd have them access files online? It makes no sense.

Anyone out there done this before?

---

### Post by Scubdup on 2009-04-16
Update

I found [these instructions]("http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate") but I get an error when executing:-

```
# modprobe dell_rbu

```

:-

```
~$ modprobe dell_rbu
FATAL: Error inserting dell_rbu (/lib/modules/2.6.28-11-generic/kernel/drivers/firmware/dell_rbu.ko): Operation not permitted

```

---

### Post by siouzi on 2009-04-17
The modprobe command requires root privileges, so try
```

sudo modprobe dell_rbu

```
It will ask for your password.

Edit: meh... you probably have tried that already, sorry :/

---

### Post by abn91c on 2009-04-17
It's** not** the BIOS you need a 64bit ubuntu version as the 32bit ubuntu will only see 3.2 gigs RAM. And it will need to be a fresh install
Look at this thread [http://ubuntuforums.org/showthread.php?p=7085502#post7085502](http://ubuntuforums.org/showthread.php?p=7085502#post7085502)

---

### Post by Scubdup on 2009-04-17
Thank abn91c. I'm using 64-bit so I'm pretty sure the problem is to do with mapping.

siouzi :redface: - I can't remember if I sudo'ed or not. Was going to keep quiet until I had a chance to test tonight!

---

### Post by Scubdup on 2009-04-22
siouzi, you were right. Sudoed modprobe and the BIOS flash worked as it should.

Which is when I found that even the newest version couldn't handle remapping and my plans for more than 3.2gb of RAM are scuppered.

Ah well.

---

