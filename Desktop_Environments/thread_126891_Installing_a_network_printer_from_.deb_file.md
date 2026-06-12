---
title: "Installing a network printer from *.deb file"
date: 2006-02-07
forum: Desktop Environments
---

### Post by DrMX on 2006-02-07
Hi all, I am a new linux user and have a question for all the experienced users in this forum.

I have a network printer that I was able to install using KUBUNTU (the driver appeared in the 'add a new printer wizard'). However I didnt like KDE that much and preferred to install Ubuntu instead.

When I try to install the printer, I do not see the right model. Lexmark t632. I had tried with KDE using the driver for the Lexmark t616 and it worked just fine. In Ubuntu, the add a printer menu shows me again the t616 but it doesnt work. THe printer makes noises as if it is printing something but then nothing comes out.

I found a driver for Debian Linux on the lexmark download driver webpage. It is a *.deb file. How am I supposed to use it? 
 
I have tried dkpg -i filename.deb and it gives me messages of uncompessing files and so on but still dont know what to do afterwards. 
Your help will be greatly appreciated. Thanks a lot

---

### Post by czayas on 2008-01-14
There is no need to install a deb file. All you need is a single PPD (Postscript Printer Description) file, that according to WhatIs.com "is a file that describes the fonts, paper sizes, resolution, and other capabilities that are standard for a particular Postscript printer. A printer driver program uses a PPD file to understand the capabilities of a particular printer".

I have the same printer at work, so I also found that the T632 is not listed when I tried to install it on Linux Mint 4.0 (Ubuntu Gutsy based) so I started googleing for "lexmark t632 ppd" (without quotes). I found a PPD file for the T632 in [http://data.versiontracker.com/drivers/manualExtract/Lexmark/Lexmark_AAG_Win2K_PS_sys_en_ext/extract/SPANISH/lmaag931.ppd](http://data.versiontracker.com/drivers/manualExtract/Lexmark/Lexmark_AAG_Win2K_PS_sys_en_ext/extract/SPANISH/lmaag931.ppd)

All you need to do is click the "Install driver" button in the New Printer assistant and direct it to the PPD file that you downloaded.

Hope this helps, two years later! :-)

---

### Post by alek01 on 2008-04-10
A usefull HowTo for Lexmark printer or any using Footmatic 2slx is on [http://foo2slx.rkkda.com/](http://foo2slx.rkkda.com/)
Good luck
Alek

---

