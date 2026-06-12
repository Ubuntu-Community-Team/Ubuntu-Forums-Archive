---
title: "Xerox DocuPrint C525A printer"
date: 2007-06-24
forum: Desktop Environments
---

### Post by cec on 2007-06-24
i am attempting to install the driver for a DocuPrint C525A printer onto my v7.04 Ubuntu system.

Driver package has been downloaded, the RPM converted via 'alien' to a '.deb' (as the RPM would not install) and then 'dpkg' run for the install...all install appeared to work fine with no error messages.

Now, CUPS Administration does not show the printer in its list (should appear under maker FX according to the instructions included with the driver package).

The printer is attached to the network.

Does anyone have experience with the installation of this printer and possibly could offer me some clues as to what I have done wrong.

Many thanks,


Charles

---

### Post by Nathan Scott on 2007-07-25
Bit late but as I found this while looking for a solution to the same problem thought Id post a reply here

New at this myself so it may not be the correct answer but once the deb is installed the easiest way to move forwards to install the printer (which I couldnt see anywhere else) is just to install the PPD directly. Just choose to install driver, and you will find the ppd in the /usr/share/cups/model/ directory.

---

### Post by popot on 2007-10-02
Apologies to the above 2 gentleman, but completeness is godliness. :)

I'm running on a P3 Dell, 312 MB Ram, Ubuntu 7.04 Feisty.  I'm setting up Fuji Xerox C525A on a network, **not USB, not parallel**.

Download Fuji Xerox C525A driver from [www.fxprinters.com](www.fxprinters.com), choose Singapore -> select Fuji Xerox C525A -> Linux.

Most likely its downloaded to your Desktop and its called dpc525a_linux_.0.0.tar.zip, and double click to unzip and untar.

In the terminal, > cd ~/Desktop/C525A_LinuxE/  and then > sudo alien Fuji_Xerox-DocuPrint_C525_A_AP-1.0-1.i386.rpm, which will covert into fuji-xerox-docuprint-c525-a-ap_1.0-2_i386.deb .
If you do not have alien, > sudo apt-get install alien

This is followed by > sudo dpkg -i fuji-xerox-docuprint-c525-a-ap_1.0-2_i386.deb

Do a 
> sudo mkdir /usr/share/ppd/cups-included/FX/ 
> sudo cp -p /usr/share/cups/model/FujiXerox/en/FX_DocuPrint_C525_A_AP.ppd /usr/share/ppd/cups-included/FX/.
*thanks to grantbuntu (msg below mine), be careful when you copy and paste, there's a space formed that cause "_C5 25_", it should be "_C525_", I'm clueless on how to rectify this. Can someone show me?

[COLOR="Red"]Add Printer using the System -> Administration -> Printing - > Add Printer -> 
Use a detected printer: FUJI XEROX DocuPrint C525 A-AP (FUJI XEROX DocuPrint C525 A-AP XXX.XXX.XXX.XXX) !If you can't see this, most likely you have not set your IP for your printer, please refer to printer instruction manual for this.
-> Forward -> Manufacturer: FX Model: DocuPrint C525 A-AP v1.0.
[/COLOR] This is wrong, might work, but it took me 15 minutes to print a 1 page document. Thanks to C525A_Linux_manE.pdf in the dpc525a_linux_.0.0.tar.zip , this is how its suppose to be done. If a dialog window asks you for your user name and password, give them the login username and password. 

Step 1,  Start firefox, URL: > [http://localhost:631/](http://localhost:631/)

Step 2, Click on the Add Printer button.

Step 3,
> Name: DocuPrint_C525_A-AP
Location:
Description:  DocuPrint_C525_A-AP
 Click continue.

Step 4, Select LPD/LPR Host or Printer from the Device menu. Click continue.

Step 5, Device URI: lpd://192.168.0.12/queue, 192.168.0.12 is the IP address of the printer. Click continue. If you have no idea what I'm talking about , please refer to printer instruction manual for this.

Step 6, > Make: FX Click continue.

Step 7, > Model: FX DocuPrint C525 A-AP vX.X(en) Click continue.

Step 8, Make sure "Printer DocuPrint_C525_A-AP has been added successfully." message is displayed. And you are done. 

Good Luck!

---

### Post by grantbuntu on 2007-10-08
There seems to be an inadvertent space in the command provided between the 5 and the 25_A ...

> sudo cp -p /usr/share/cups/model/FujiXerox/en/FX_DocuPrint_C5 25_A_AP.ppd /usr/share/ppd/cups-included/FX/

should be 

```
sudo cp -p /usr/share/cups/model/FujiXerox/en/FX_DocuPrint_C525_A_AP.ppd /usr/share/ppd/cups-included/FX/
```

Strangely, if you wrap the exact same quote with QUOTE it puts the space back??!!??:confused: so I can see how this happened to popot.

---

### Post by ranger_cole on 2008-05-09
When I run this command
sudo mkdir /usr/share/ppd/cups-included/FX/ 

I get
jaypugh@jaypugh-desktop:~$ sudo mkdir /usr/share/ppd/cups-included/FX/ 
mkdir: cannot create directory `/usr/share/ppd/cups-included/FX/': File exists

I checked the for the printer and it not listed.  Only the 1320 c is listed not he fuji one.  Thanks for helping a newbie.

---

### Post by fisho on 2008-06-03
thanks man worked perfect

---

### Post by popot on 2008-06-24
> **ranger_cole said:**
> When I run this command
sudo mkdir /usr/share/ppd/cups-included/FX/ 

I get
jaypugh@jaypugh-desktop:~$ sudo mkdir /usr/share/ppd/cups-included/FX/ 
mkdir: cannot create directory `/usr/share/ppd/cups-included/FX/': File exists

I checked the for the printer and it not listed.  Only the 1320 c is listed not he fuji one.  Thanks for helping a newbie.

Ok, skip sudo mkdir /usr/share/ppd/cups-included/FX/ . Run the rest!

---

