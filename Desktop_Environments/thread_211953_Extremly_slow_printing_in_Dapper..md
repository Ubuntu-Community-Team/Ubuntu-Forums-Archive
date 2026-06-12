---
title: "Extremly slow printing in Dapper."
date: 2006-07-09
forum: Desktop Environments
---

### Post by theseal666 on 2006-07-09
Hello, trying again, been searching the ubuntuforum and the net without success.

I have an USB HP Officejet V40 installed in my Dual PIII 1GHz system, Dapper works as a charm but printing is EXTREMLY slow, printing one page takes up to 15 minutes!!(the inc has plenty of time to dry :P)

I have installed and compiled the latest HPLIP from the hlip website, the version packed in dapper do not work at all.
Cups is also installed and I can se the printer/jobs/settings, so basicly it works fine, except from the printing beeing extremly slow.

any tips?

---

### Post by eniacpx on 2006-07-15
I am having the same issue with a Canon ip3000, anybody have any clues?

---

### Post by Staz69uk on 2006-07-25
I'm seeing the same with a Canon ip1500.

---

### Post by Staz69uk on 2006-07-25
> **Staz69uk said:**
> I'm seeing the same with a Canon ip1500.

I'm now looking at bug #34599 which seems to be related.

---

### Post by Staz69uk on 2006-07-25
> **Staz69uk said:**
> I'm now looking at bug #34599 which seems to be related.

Well, after several hours of frustration I can now print (in draft quality) at reasonable speed using TurboPrint [[http://www.turboprint.info/turboprint.html]](http://www.turboprint.info/turboprint.html]).  I suppose that I could pay the $30 for the registered version and get decent quality as well.

However, I'd really like to know why TurboPrint works fine (using Cups and usb://Canon/iP1500) whereas the basic support doesn't (using Cups and usb://Canon/iP1500).

Printing is *really* slow; >20 minutes per page.  
It starts off fast enough, but after 1/3 page it slows to a crawl.
	CPU utilisation remains very low.
	Data light on printer continually flashing

Printing a one line text file from GEdit is fast though.  It looks to me like the driver fills a buffer and sends the contents quickly enough, but once the initial buffer has been sent something goes wrong when the printer requests more data.

Other information...

I'm using Ubuntu Dapper (6.06), fully up to date.  cupsys package version is "1.2.1-0ubuntu2".  The printer is connected via a USB 1 port.

I have re-installed all the CUPS packages I could find...
cupsys (version 1.2.1-0ubuntu2) will be re-installed
cupsys-bsd (version 1.2.1-0ubuntu2) will be re-installed
cupsys-client (version 1.2.1-0ubuntu2) will be re-installed
cupsys-driver-gutenprint (version 5.0.0~rc2-0ubuntu6) will be re-installed
foomatic-db (version 20060408-1ubuntu1) will be re-installed
foomatic-db-engine (version 3.0.2-20060318-1ubuntu1) will be re-installed
foomatic-db-gutenprint (version 5.0.0~rc2-0ubuntu6) will be re-installed
foomatic-db-hpijs (version 1.5-20060318-1) will be re-installed
foomatic-filters (version 3.0.2-20060318-2) will be re-installed
foomatic-filters-ppds (version 20060406-0ubuntu1) will be re-installed
gnome-cups-manager (version 0.31-1.1ubuntu13) will be re-installed

From [http://lists.freestandards.org/pipermail/printing-user-canon/2005/002359.html](http://lists.freestandards.org/pipermail/printing-user-canon/2005/002359.html) ...
[I]	When using CUPS administration select USB Printer
	#1 with status readback for Canon BJ (Canon iP1500) and the canon
	category Canon PIMA iP1500 Ver.2.50 (en).[/I]

Unfortunately, I have had real trouble getting gnome-cups-manager to save settings, even when I run it using sudo.  Also, when I have managed to get it to use the "USB Printer #1 with status readback for Canon BJ (Canon iP1500)" port, it won't print at all.  According to the cups config file this is connected to canon_usb:/dev/usblp0 but I don't know what that means.  Does the "lp0" bit imply some sort of parallel port emulation?

Some other links...
[http://linux.cergynux.net/canon/](http://linux.cergynux.net/canon/)
[http://bigblue.res.cmu.edu/mediawiki/index.php/Laserjet_6p](http://bigblue.res.cmu.edu/mediawiki/index.php/Laserjet_6p)
[http://www.ubuntuforums.org/showthread.php?t=38995&highlight=Pixma+ip4000](http://www.ubuntuforums.org/showthread.php?t=38995&highlight=Pixma+ip4000)
[http://www.ubuntuforums.org/showthread.php?t=93265](http://www.ubuntuforums.org/showthread.php?t=93265)
[http://www.lowlevel.cz/log/pivot/entry.php?id=40](http://www.lowlevel.cz/log/pivot/entry.php?id=40)

Final point; I also stumbled across a reference to the "bjcups" command which is used to configure/maintain the printer.  Very useful.

---

### Post by gffgjh on 2006-07-26
My HP LaserJet 1022 was also print slo.. .w. Works now better when I installed usb 2 card to computer. I heard some where that driver send pages on bitmap.. And thats why usb 1.1 are too slow.

---

