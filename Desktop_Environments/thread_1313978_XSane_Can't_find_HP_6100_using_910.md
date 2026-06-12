---
title: "XSane Can't find HP 6100 using 910"
date: 2009-11-04
forum: Desktop Environments
---

### Post by bluman on 2009-11-04
Hi there,

I would like to contribute the solution I found (with the help of this post [http://ubuntuforums.org/archive/index.php/t-112364.html](http://ubuntuforums.org/archive/index.php/t-112364.html)) to get XSane to find my network scanner after formatting 904 and installing 910. XSane failed to find my HP Photosmart C6180 All-in-One device. With 904 it just worked out of the box!

First you must know the IP address of your network scanner. I'm using the 10/100 wired connection not 802.11 wireless.

Use the following command to generate the correct SANE URI.

hp-makeuri <IP address of scanner>

Example:
root@mark-desktop:/etc/sane.d# hp-makeuri 192.168.245.6

HP Linux Imaging and Printing System (ver. 3.9.8)
Device URI Creation Utility ver. 5.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

CUPS URI: hp:/net/Photosmart_C6100_series?ip=192.168.245.6
SANE URI: hpaio:/net/Photosmart_C6100_series?ip=192.168.245.6
HP Fax URI: hpfax:/net/Photosmart_C6100_series?ip=192.168.245.6

Done.

Then use the SANE URI as follows:

xsane "hpaio:/net/Photosmart_C6100_series?ip=192.168.245.6"

To make this permanent when accessing XSane from the Graphics menu:

- right-click on the "Applications" menu at the top-left of your Ubuntu desktop.

- select "Graphics" on the left-hand frame

- click "XSane Image scanning program" then click "Properties" to the right.

- in the "Command" field add the full command line as used above.
xsane "hpaio:/net/Photosmart_C6100_series?ip=192.168.245.6"

- click "Close" then "Close" again.

Now if you select "Applications->Graphics->XSane Image scaning program" your XSane should open and access your network scanner correctly.

I hope this saves someone a little time.

---

### Post by coffeecat on 2009-11-04
Thanks for posting this useful information.

I'm using a HP C6310 all-in-one network device - wired connection. With Jaunty, xsane didn't work quite out of the box for me. When I opened xsane first I got a "no scanning device found" or words to that effect. Later on, I went to Administration > Printing to set up the printer and cups found and configured it without problem - it detected the IP address automatically. And then when I went back to xsane it found the scanner quite happily. So it seems that if the printer has been configured, xsane will detect the scanner, but if not, it doesn't. I'm sure there's a logical explanation. :-k

The same thing happened on two other computers, so it wasn't a one-off happening. In fact, I'd already discovered this trick in an earlier release - could even be as far back as Hardy - and I found I had to do the same in Jaunty.

> **bluman said:**
> hp-makeuri <IP address of scanner>

Example:
root@mark-desktop:/etc/sane.d# hp-makeuri 192.168.245.6


One problem I found is that the HP machine defaulted to DHCP so, when I switched on the various networked machines in a different order, the OfficeJet was assigned a different IP. So cups and xsane couldn't find it unless I reconfigured. Which was a pain. (MacOS does **not** have this problem [/rant] ). So I setup the HP with a static address, not helped by the inadequate HP documentation which made no mention of the web-based configuration interface which I found almost as a desperate last measure.

Anyway - thanks for the post. I haven't yet tried printing or scanning with the HP with Karmic, so this information is going to come in useful.

---

### Post by coffeecat on 2009-11-04
Just an update. I've set up my HP machine now in Karmic. I found the same "trick" that worked in Hardy > Jaunty works in Karmic.

If you go to Xsane first it won't detect the scanner. So, go to Administration > Printing, let it detect the network printer, install it and print a test page. Now go to Xsane and the scanner is detected and works.

---

### Post by DenysT on 2009-11-05
> **coffeecat said:**
> Just an update. I've set up my HP machine now in Karmic. I found the same "trick" that worked in Hardy > Jaunty works in Karmic.

If you go to Xsane first it won't detect the scanner. So, go to Administration > Printing, let it detect the network printer, install it and print a test page. Now go to Xsane and the scanner is detected and works.

If only it worked that well with Epson also. 9.04 refuses to even find the Artisan 700 scanner even though it finds and uses the printer flawlessly and in 9.10 Xsane always returns "Failed to start scanner: Error during device I/O".

---

### Post by coffeecat on 2009-11-05
I've no experience of Epson scanners, so I'm fishing in the dark here

Have you tried connecting the device with USB rather than through the network? If it works with USB, then it's unlikely to be a driver problem. If it doesn't then... well I don't know.

According to the [relevant sane project page]("http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-EPSON") your scanner is supported in Linux, so it *ought* to work. Has a google search thrown up anything vis a vis this scanner and Jaunty/Karmic?

The only other thing I can suggest is to set your Epson with a fixed IP address. I can't remember whether I discovered my set-up-the-printer-first trick before or after I set a fixed IP address for the HP. Having a wandering IP address with DHCP is just another variable/complication in this situation.

---

### Post by DenysT on 2009-11-05
> **coffeecat said:**
> I've no experience of Epson scanners, so I'm fishing in the dark here

Have you tried connecting the device with USB rather than through the network? If it works with USB, then it's unlikely to be a driver problem. If it doesn't then... well I don't know.

According to the [relevant sane project page]("http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-EPSON") your scanner is supported in Linux, so it *ought* to work. Has a google search thrown up anything vis a vis this scanner and Jaunty/Karmic?

The only other thing I can suggest is to set your Epson with a fixed IP address. I can't remember whether I discovered my set-up-the-printer-first trick before or after I set a fixed IP address for the HP. Having a wandering IP address with DHCP is just another variable/complication in this situation.

I assigned a static IP from the get go and wired the sucker. Wireless is too unreliable and I knew DHCP could cause problems. The scanner is found by 9.10 at the correct IP, it just doesn't scan. 9.04 doesn't even find the scanner. Works great with XP on the network. I can send print jobs to it from either Linux or XP just fine. In the mean time I have hooked up my old Epson Perfection 1200 to the 9.10 PC as it still works. However, I'll try connecting the Artisan 700 via USB to the 9.04 and see what happens and post my results.

Every search I do on the net always leads to the same dead end. The drivers page for Avasys or Sane Backends. I have voiced my displeasure with Epson via e-mail for their lack of support for Linux.

---

### Post by ub12 on 2009-11-16
Thanks bluman,
Your instructions work for me. I was having a problem scanning with Photosmart 3300.

cheers

---

### Post by hobbitman on 2010-01-13
Thanks bluman,

Your solution worked fine for me too. After a fresh install of Koala on my Compaq Presario laptop, I wanted to see if printing and scanning could be made working.
I have a HP Officejet Pro L7590 with a fixed IP address. The printer was recognized automatically. I could print a test page without a problem.
After that I tried to perform a scan and got the message : no device available.
So coffecat's solution did not work for me.
After the hp-makeuri command with the ip-address I got the URI:
hpaio:/net/Officejet_Pro_?L7500?ip=192.168.1.100
with which i could start xsane, in good working order. ;)
Thanks again!

Hobbitman

---

### Post by oshunluvr on 2010-02-12
I case anyone wants to know another way to address this:

sudo kate /etc/sane.d/dll.conf

remark out all lines EXCEPT "net" and "hpaio"

sudo kate /etc/sane.d/net.conf

add the ip address of the scanner server at the end

that should do it

---

### Post by nikkkko on 2010-02-15
What if you can print but can't scan AND makeuri doesn't work ?!

HP Linux Imaging and Printing System (ver. 3.9.8)
Device URI Creation Utility ver. 5.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Device not found

---

### Post by gypaete09 on 2013-01-03
Perfect!

Switching Ubuntu versions and installing a new PC makes every thing that worked already, a new problem - thank you for the solution! ):P

---

