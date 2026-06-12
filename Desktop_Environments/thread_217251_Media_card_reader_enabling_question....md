---
title: "Media card reader enabling question..."
date: 2006-07-16
forum: Desktop Environments
---

### Post by kayabilly on 2006-07-16
Hi everyone...I hope I am in the right forum...I'm definitely a noob at Linux...but I can build my own PC (with Windows), so not a complete noob...installed the new dapper drake...got my second sata drive to mount following online guides...everything is going fine so far...Quick question (one of many I'm sure)...I have a HP 7350 printer that has a built in card reader,  and wanted to know how I can get it to work...the printer itself works fine...My first instict is always to use Google first but the results didn't help this time...I'm hoping to get proficient with dapper so I can finally end my divorce with windows once and for all...thanks

---

### Post by kayabilly on 2006-08-07
Anyone?

---

### Post by ShamusPatt on 2006-11-24
I tried GOOGLE as well - it didn't help much with this one (but it brought up your post, so I'll fill it in).

I found the answer through [http://www.linuxprinting.org/](http://www.linuxprinting.org/), which led me to the HPLIP package. I discovered that I already had it installed on my Ubuntu system; if you don't, just search for it and install it with Synaptic. It looks like HPIJS is the usual driver installed for the 7350 but you can use HPLIP instead which is a larger package (including HPIJS) and which gives you access to the extra goodies on the printer e.g. the card reader.

The command you want is called hp-photo . It works a bit like smbclient in that it has a simple script interface that lets you do directory listings, copy files to and from the card etc. If you just run it with no args, it will look for your printer and connect to it.

Kudos to HP for providing such great Linux support. They seem to be a major contributor to HPLIP. The driver development page is on SourceForge at [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/).

---

