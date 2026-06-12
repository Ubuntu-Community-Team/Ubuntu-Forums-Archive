---
title: "Epson Stylus Photo r300"
date: 2005-12-15
forum: Desktop Environments
---

### Post by AudioMove on 2005-12-15
Im trying to install my **epson stylus photo r300** in Kde and get as far as the **printer test** in the printer configuration utility. This has been bugging me for quite some time just was never willing to admit to defeat till now :D 

Ive tryed both drivers Cups and Foomatic but fail. Fail is in the test page never prints. 

dmesg - brings up some strange messages 

**4296908.561000] usb 4-2: device descriptor read/64, error -71**

That statement is repeated quite frequently. Anyone fill me in on what that means? My optical mouse works fine in any usb port so i fail to see that there something wrong with my usb ports and the printer works fine on my win laptop and other desktop running Fedora. 

Anyone has any suggestions or need further info please post.

Thx
Cathal

---

### Post by emperor on 2005-12-15
[quote=AudioMove]Im trying to install my **epson stylus photo r300** in Kde and get as far as the **printer test** in the printer configuration utility.

Thx
Cathal[/quote] 
I use Gnome not KDE!

Have you installed the cups gimp-print drivers?

You should see a R300/310 printer selection under the Epson printer selection list.

Printer test page printer OK on my i9300 with Breezy.

I did find that the Epkowa drivers on the japanese site do not work at all on Ubuntu 5.10.

I had printer set up as a local printer.

---

### Post by AudioMove on 2005-12-15
I have using Gnome for a long time, just moved over to KDE recently. UNfortunately didnt work in Gnome either. Yea my set up is very similar to what you've stated, gimp print drivers are installed also.

---

### Post by emperor on 2005-12-15
The R300 has a USB2 interface. I have only tried it with a USB2 port, but  I would expect it to work on a standard USB port as well.

Are you using an external USB hub, or connected directly to your computer?

---

### Post by AudioMove on 2005-12-15
connected directly to computer

---

### Post by AudioMove on 2005-12-15
I have a usb2 card (i think its usb2) around somewhere. I might stick that into my desktop

---

### Post by emperor on 2005-12-15
Does "lsusb" show the printer as connect to a USB port?

Output on my machine: 
Bus 005 Device 003: ID 04b8:0803 Seiko Epson Corp.

---

### Post by AudioMove on 2005-12-15
No, Only shows my mouse, sry should of mentioned that earlier.

---

### Post by emperor on 2005-12-15
[quote=AudioMove]No, Only shows my mouse, sry should of mentioned that earlier.[/quote]

Then putting that USB2 adapter in your machine may be the solution!

---

### Post by AudioMove on 2005-12-16
Will put in that adapter today, will be interesting to know if it needs usb2 to work.

---

### Post by teaker1s on 2005-12-16
this may point you in right direction 
[http://www.ubuntuforums.org/showthread.php?t=85283](http://www.ubuntuforums.org/showthread.php?t=85283)

---

### Post by emperor on 2005-12-16
[quote=teaker1s]this may point you in right direction 
[http://www.ubuntuforums.org/showthread.php?t=85283]("http://www.ubuntuforums.org/showthread.php?t=85283")[/quote] 
I found that the drivers from Epson's japanese site for the R300 do not work.
[http://www.avasys.jp/english/linux_e/dl_ink.html](http://www.avasys.jp/english/linux_e/dl_ink.html)

Tested on both Ubuntu 5.10 and Fedora Core 2. The cups gimp-print drivers do work!

---

### Post by AudioMove on 2005-12-16
Ill take a look at the driver anyway, I've installed my usb2 adapter and the printer still won't print.

**Update:** Still no luck with that driver, printer still refuses to print.

---

### Post by emperor on 2005-12-16
These packages will add support to read the ink level.

1. I created an inklevel pkg using checkinstall from here:
[http://libinklevel.sourceforge.net/](http://libinklevel.sourceforge.net/)

You will need to install libieee1284 from Ubuntu repo first.
Then install the 0.6.5rc1 version which is gcc4 compatible.
You will get warning during make but no fatal errors.
Use checkinstall to install and make ".deb".

2. commandline inklevel check utility:
[http://ink.sourceforge.net/](http://ink.sourceforge.net/)

3. gnome gui for inklevel:
[http://gmso.linux-sevenler.org/down.php?lang=en](http://gmso.linux-sevenler.org/down.php?lang=en)

Note: Use hwinfo package from gmso site instead of newer Debian package in Ubuntu repo. Need libhd.so.8 which is missing from Ubuntu package.

---

### Post by emperor on 2005-12-16
[quote=AudioMove]Ill take a look at the driver anyway, I've installed my usb2 adapter and the printer still won't print.

**Update:** Still no luck with that driver, printer still refuses to print.[/quote]

In "Printers", is 

Model: Stylus Photo R300
Driver: "gimp-print"
Printer Type set to: "Network Printer - CUPS (IPP)
URI: usb://EPSON/Stylus Photo R300

---

### Post by AudioMove on 2005-12-17
I have everything except the uri. I assign it to a default usb port. It doesnt pick up the printer so doesnt list when choosing the uri.

---

