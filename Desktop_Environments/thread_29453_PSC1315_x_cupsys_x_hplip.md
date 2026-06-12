---
title: "PSC1315 x cupsys x hplip"
date: 2005-04-24
forum: Desktop Environments
---

### Post by dangerous666 on 2005-04-24
I can't make my new multifunction(printer/scanner)  work at all... After days trying on, I decide do post a thread here.

First of all, I have cupsys running, and I can access the web interface through localhost:631... But i can't get to the adminstrative issues, cause It asks for user/password.. tryed root, user, etc... (And I had already created a user called cupsys in the shadow group).. I had already restated cupsys, rebooted the computer and no success... I can't add/remove printers through this interface...

No problem, there's kcontrol...its printer wizard communticates to the cupsys and I was able to add my printer, just downloading the driver (at linuxprinting.org)... After installing I can't even print the test page :(...Accessing the web interface of cups, the printer was there...

I think the printer/scanner is detected correctly by the system, cause running lsusb the it appears...It also appears in the kinfocenter...

Ok.. I decide to try Hplip.. I downloaded and installed the package 0.8.7 avaliable at hoary repos. No success, I cant access the gui... The toolbox program runs without GUI (like background running)... There's a tip on this forum about this GUI problem but it didn't work for me...

So, I decided to download the source of the last version of the hplip (0.9.2)... After solving some dependencies I installed hplip succesfully... But running the toobox aplication (Now, the GUI appears) It can't detect my printer... A dialog says that no HP device found... In he same dialog a tip says that only devices installed through the cups web backend will be detected.. Yes, I installed my printer using kcontrol.. but the printer appears perfectly in the cups web interface... (after I had installed hplip I first uninstalled the printer installed previously and installed it again with hplip drivers, as I saw in a thread at this forum)

So It's the problem.... At last I installed xsane, sane-utils and some more to at least make my scanner work... No success again, Xsane do not detect any device....

Any help will be appreciated... Thanx

---

### Post by kkvenkit on 2005-04-25
Have you tried the instructions at [http://www.ubuntulinux.org/wiki/HpPsc1200series](http://www.ubuntulinux.org/wiki/HpPsc1200series)?

---

### Post by dangerous666 on 2005-04-25
[QUOTE=kkvenkit]Have you tried the instructions at [http://www.ubuntulinux.org/wiki/HpPsc1200series](http://www.ubuntulinux.org/wiki/HpPsc1200series)?[/QUOTE]

Yes, but it doesn't work... :(

After installing hpoj, running "sudo /etc/init.d/hpoj setup" it returns the following:

Probing "/dev/usb/lp0"...
    *** Found "psc 1310 series " but failed to communicate with it!
    *** Elapsed time for this attempt was 0 second(s).
    *** Check syslog file for ptal-mlcd error messages.
    *** See hpoj documentation for troubleshooting information.

At the end of the process..

Starting the HP OfficeJet Linux driver.
    No hpoj devices have been configured.
    As root, run "/etc/init.d/hpoj setup".

I can see the printer running lsusb and at kinfocenter...

Adding a new printer, acording to the tip "entry beginning with "PTAL". Mine is "PTAL devices not found"

EHEHEH... i think I have a great probem here...

At the end, I can add the printer, it appears at cup backend... But I cannot print anything...

Thanx for the help, but I need more... hehee

---

### Post by dangerous666 on 2005-06-20
Hey people... I was able to put my printer working through hpoj/hpijs (don't remember how) but now I made a fresh install of hoary and the previous problem (the thread above) is back again... The same situation... Can anyone help me?

---

### Post by dejitarob on 2005-06-21
I have the same printer. The 1310 driver works for all the 131x series. In fact, if you goto HP's website for windows drivers, that is what you download. Anyways, all I had to do was goto Control Center, Peripherals, Printers, Add, Printer, Local (network if its networked), Select the port (address if its networked), Selected HP, and then selected PSC1310 hpijs. Works like a charm. I haven't messed around with the scanner at all. The last time I tried in Gnome I didn't have any luck.

---

### Post by dangerous666 on 2005-06-21
[QUOTE=dejitarob]I have the same printer. The 1310 driver works for all the 131x series. In fact, if you goto HP's website for windows drivers, that is what you download. Anyways, all I had to do was goto Control Center, Peripherals, Printers, Add, Printer, Local (network if its networked), Select the port (address if its networked), Selected HP, and then selected PSC1310 hpijs. Works like a charm. I haven't messed around with the scanner at all. The last time I tried in Gnome I didn't have any luck.[/QUOTE]

It works for me too... But I'd like to have my printer working under hplip...

Thanx!

---

### Post by dejitarob on 2005-06-21
Whys that whats the difference?

---

### Post by dangerous666 on 2005-06-22
[QUOTE=dejitarob]Whys that whats the difference?[/QUOTE]

Cause Hplip seems to be more powerfull, It's a centralized, lots of maintenance tools, etc...

---

### Post by mr_ed on 2005-06-23
[QUOTE=kkvenkit]Have you tried the instructions at [http://www.ubuntulinux.org/wiki/HpPsc1200series](http://www.ubuntulinux.org/wiki/HpPsc1200series)?[/QUOTE]

This is now [https://wiki.ubuntu.com/HpPscHpPhotosmartSeriesAllInOnePrinters](https://wiki.ubuntu.com/HpPscHpPhotosmartSeriesAllInOnePrinters)

---

### Post by dangerous666 on 2005-06-23
[QUOTE=mr_ed]This is now [https://wiki.ubuntu.com/HpPscHpPhotosmartSeriesAllInOnePrinters](https://wiki.ubuntu.com/HpPscHpPhotosmartSeriesAllInOnePrinters)[/QUOTE]

Yes... and it works... but I want to use HPlip! Not HPOJ & HPIJS....

---

### Post by Shiven on 2005-07-27
[https://wiki.ubuntu.com/HpPscHpPhotosmartSeriesAllInOnePrinters?highlight=%28printer%29](https://wiki.ubuntu.com/HpPscHpPhotosmartSeriesAllInOnePrinters?highlight=%28printer%29)

Instructions to install hplip ^-^ 

Hope this helps!

Shiven

---

