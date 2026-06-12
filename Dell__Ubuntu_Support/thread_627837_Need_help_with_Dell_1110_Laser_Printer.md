---
title: "Need help with Dell 1110 Laser Printer"
date: 2007-11-30
forum: Dell  Ubuntu Support
---

### Post by Holleywood on 2007-11-30
I read all of the recommended threads and downloaded the rpm package for the samsung printer, converted it to a deb package, but cannot get it to install. The print jobs will go to the printer, which is recognized, and the job light blinks but nothing after that. Please advise. Thanks.

---

### Post by gridlok on 2007-12-09
Have you tried using the Samsung 1200 printer drivers already loaded in Ubuntu. That is the driver I use for my printer and have had no noticeable issues with printing.

---

### Post by chender on 2008-01-02
I have the same issue with the Dell 1320c.  No drivers around.  I located one reference to a Fuji Xeros driver, but that resulted in the printer flashing and not printing too.  Anyone out there have, or could amend a driver for us to work on lower level, yet brand new Dell Printers?  

Thanks in anticipation.

---

### Post by skleed on 2008-01-06
The printer is actually made by Fuji-Xerox.  I found an rpm on another site, here is what I did (takes about 10 minutes):

Use an ftp client to go to 

ftp.fxa.com.au

Log in anonymously.

Navigate to drivers/dpc525a/dpc525a_linux_.0.0.tar.zip

Get this file, and the pdf of the similar name.

The PDF instructions did not quite work for me, so this is what I did.

Move the file to a permanent home:
```
 sudo mv dpc525a_linux_.0.0.tar.zip /usr/local/src
```

Unzip the file:
```
sudo unzip dpc525a_linux_.0.0.tar.zip
```

Get alien so that you can convert the RPM (RedHat, SUSE, Fedora package format) into a deb file (Ubuntu package):
```
sudo apt-get install alien
```

Change directory into the one with the RPM:
```
cd C525A_LinuxE
```

Convert the RPM:
```
sudo alien Fuji_Xerox-DocuPrint_C525_A_AP-1.0-1.i386.rpm
```

Install the deb package so that drivers are available to your printer:
```
sudo dpkg -i fuji-xerox-docuprint-c525-a-ap_1.0-2_i386.deb
```

Now you are ready to install the printer.  Plug it in to an available USB port, and follow the wizard.

For the Printer manufacturer, choose FX.

There is only one driver listed under that manufacturer, it should be the c525 driver.

My install defaulted to printing everything from the bypass tray, you can change this in the printer options.

Good luck!

---

### Post by louisgag on 2008-05-19
> **gridlok said:**
> Have you tried using the Samsung 1200 printer drivers already loaded in Ubuntu. That is the driver I use for my printer and have had no noticeable issues with printing.

Thank you! That's the only thing that worked for me under ubuntu 7.10. (I had tried the spix driver with no success).

:popcorn:

---

