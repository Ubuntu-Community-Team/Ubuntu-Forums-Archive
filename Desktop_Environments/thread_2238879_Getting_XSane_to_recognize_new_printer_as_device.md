---
title: "Getting XSane to recognize new printer as device"
date: 2014-08-10
forum: Desktop Environments
---

### Post by george-domijan90 on 2014-08-10
I recently changed Canon printers, and have been able to establish a wireless printer connection, but my XSane scanning program cannot find a device.  Any ideas on how to get it to recognize my Canon MG 5520 printer?

---

### Post by pdc on 2014-08-10
for Xsane to see the printer, the sane-pixma backend has to have it recognised; with a very recent printer, it is not in their database yet; they do need access to the hardware, so they need testers;

eg I see > PIXMA MG5500 Series 	[COLOR="#EE82EE"]USB 	0x04a9/0x1771[/COLOR] 	[COLOR="#008000"]Unteste[/COLOR]d 	[COLOR="#0000FF"]Testers needed[/COLOR]!

from here [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) so if you look on that page, **they would be delighted if you help them** and they could ensure you get the latest version of sane..........you; crucially; have the hardware to help them; many volunteers in linux;

___________________

if you want to scan before then, Canon release [COLOR="#0000FF"]ScanGearMP[/COLOR] to drive the scanner side of your device

If you go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100552302.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100552302.html) and click to download and SAVE you will get scangearmp-mg5500series-2.20-1-deb.tar.gz

commands to copy and paste into a terminal; line by line; hitting ENTER after each paste ..............are..............

[COLOR="#FF0000"]cd Downloads
tar -zxvf scangearmp-mg5500series-2.20-1-deb.tar.gz
cd scangearmp-mg5500series-2.20-1-deb
./install.sh[/COLOR]

and to run [COLOR="#0000FF"]ScanGearMP[/COLOR] initially it is done from the terminal with > [COLOR="#FF0000"]scangearmp[/COLOR] and if all works well, you set up a launcher .............how to will follow if you want that ..............

---

