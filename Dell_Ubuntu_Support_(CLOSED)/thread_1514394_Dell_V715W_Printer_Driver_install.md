---
title: "Dell V715W Printer Driver install?"
date: 2010-06-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Karl10 on 2010-06-20
[FONT="Comic Sans MS"][SIZE="4"][/SIZE][/FONT]Hi Folks

Having a little difficulty installing a Dell V715W 'all-in-one' wireless printer.  I found the appropriate driver on the Dell site and downloaded it, along with the 'readme.'  All good, so far.  Instructions are to run the unpacked file in Terminal.  Ok... fired up Terminal and it 'morphed' into a graphical-looking mini-install program.  Got about three screens into it, and it pops up a dialogue box asking for the root (administrative) password; no problem, typed it in... and it refuses to accept it; kicks back a message box "Incorrect password given, please re-type."  About the twentieth time I tried this, I became convinced that it was not my typing at fault.

When I log in, I use a password.  It is the same password I use when I use a 'sudo' command and Terminal prompts me for the admin password.  Am I way off base, here, or is it possible to have my user password AND my admin password be the SAME word??  If not, this would explain the install applet's "bad behavior." 

I tried calling Dell, but they don't want to help 'cuz the laptop didn't ship with Ubuntu as the OS (I got it with Win7 so I could do games, and added Ubuntu in a grub-loaded dual-boot).  Never did much care for Dell (it's my wife's laptop/printer combo; I'm just trying to tap in to the printer as it's now our only printer.)

By the way, I'm running 10.04LTS "lucid lynx."  Machine is an ASUS G73JH-A1, 8Gb RAM, i7 Quad-core CPU, ATi Mobility Radeon HD 5870 GDDR5 1024MB, 2 500Gb SATA hard drives, Blu-ray optical drive. Win7 64-bit, and 64-bit Ubuntu as well.

Any thoughts or suggestions gratefully accepted!

Karl Harris
Bristol, NH

---

### Post by mikewhatever on 2010-06-21
Run **sudo -i** to become root before running the installer. It should not ask for passwords this time.

---

### Post by neptasur on 2010-08-14
I am having the same issue installing a Lexmark in 9.10.  I did run sudo -i as suggested by "mikewhatever", but it did not work.

Any other ideas?

Thank you,

Neptasur

---

### Post by Hakunka-Matata on 2010-09-27
this is copied out of: [https://answers.launchpad.net/ubuntu/+source/cups/+question/122664]("https://answers.launchpad.net/ubuntu/+source/cups/+question/122664")

using Terminal, CD into the folder where your dell driver file resides, my driver file was: dell-inkjet-09-driver-1.0-1.i386.deb.sh and it was located in the Desktop folder, therefore I used the command listed below.  Terminal then stared the dell installation as usual, it may ask for your Ubuntu password, but the dell installer did NOT ask for a password this time around, it worked beautifully.  Use the above listed launchpad.net URL to see the source of my comments here.  Good Luck 

cd ~/Desktop/; chmod +x ./dell-inkjet-09-driver-1.0-1.i386.deb.sh; gksudo ./dell-inkjet-09-driver-1.0-1.i386.deb.sh

Should do it.

---

### Post by Karl10 on 2010-12-17
Many thanks, Hakuna-M !!   Worked like magick!   How long does it generally take to get so comfortable in Ubuntu?

Karl

---

### Post by ckyfreak1025 on 2011-01-11
Has anyone had any luck installing this printer on 10.10 64-bit? The most recent driver from Dell will abort because it is not 32-bit. Has anyone found alternative drivers, or perhaps a driver form the actual manufacturer (since all Dell printers are just rebranded)?

---

### Post by ckyfreak1025 on 2011-01-30
Bump?

---

### Post by andrea.dic on 2011-02-14
I have a P713W Dell printer and 10.10 Ubuntu and I had the same problems (root pswd not recognized during the graphic installation). I downloaded the driver (Dell website, dell-inkjet-09-driver-1.0-1.i386.deb.sh, R294166.tar.gz) but I needed to be root (the password did not work) allowing also to disable access to the screen.
So to install the driver 

xhost +
sudo -i 

and then run the installer normally

---

### Post by SVWander on 2011-12-08
It seems this is an ongoing problem with this Dell program. I have tried to use:
xhost +
sudo -l
and then run: sh dell-inkjet-09-driver-1.0-1.i386.deb.sh
that starts the Dell driver program but when it asks for the root password it will not accept it. Nothing I have tried can get me pass this road block. Can anyone give me any ideas on how to install these drivers?

---

### Post by dantrevino on 2012-04-19
Does anyone have a copy of the driver files?  I have a friend with this printer and the Dell website is full of #fail.

tia,
dan

---

### Post by cabz on 2012-05-21
I tried to run the "cd command for my install and it errored out. on the install it asked for my password but not the root password. P.S i am installing in ubuntu 12.04


.i386.deb.sh; gksudo ./dell-inkjet-09-driver-1.0-1.i386.deb.sh
Verifying archive integrity... All good.
Uncompressing nixstaller.........................................................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86
TRACKING IDENT = 140509
cpu speed = 1667 MHz
ram size = 991.0703125 MB
hd avail = 88259 MB
dpkg: error processing dell-inkjet-09-driver-1.0-1.i386.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 9 package 'dell-inkjet-09-driver':
 blank line in value of field 'Description'
Errors were encountered while processing:
 dell-inkjet-09-driver-1.0-1.i386.deb

---

### Post by cabz on 2012-05-21
I just tryed to install the driver for my 715w in xubuntu 12.04 and it was a no go.

here is the terminal view can anyone make any sense of it?

cabz@cabz-Inspiron-1012:~$ cd ~/Desktop/; chmod +x ./dell-inkjet-09-driver-1.0-1.i386.deb.sh; gksudo ./dell-inkjet-09-driver-1.0-1.i386.deb.sh
Verifying archive integrity... All good.
Uncompressing nixstaller.........................................................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86
TRACKING IDENT = 140509
cpu speed = 1667 MHz
ram size = 991.38671875 MB
hd avail = 88802 MB
dpkg: error processing dell-inkjet-09-driver-1.0-1.i386.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 9 package 'dell-inkjet-09-driver':
 blank line in value of field 'Description'
Errors were encountered while processing:
 dell-inkjet-09-driver-1.0-1.i386.deb
cabz@cabz-Inspiron-1012:~/Desktop$ cd ~/Desktop/; chmod +x ./dell-inkjet-09-driver-1.0-1.i386.deb.sh; gksudo ./dell-inkjet-09-driver-1.0-1.i386.deb.sh

---

### Post by cabz on 2012-05-21
> **dantrevino said:**
> Does anyone have a copy of the driver files?  I have a friend with this printer and the Dell website is full of #fail.

tia,
dan

[http://www.dell.com/support/drivers/us/en/04/DriverDetails/DriverFileFormats?c=us&s=bsd&cs=04&l=en&DriverId=R247653](http://www.dell.com/support/drivers/us/en/04/DriverDetails/DriverFileFormats?c=us&s=bsd&cs=04&l=en&DriverId=R247653)

---

### Post by DiStefano on 2012-06-23
I am also encountering the abovementioned error referred to by cabz. Is there any information on how this can be solved?

Kind regards,
Fabian

---

### Post by Mysticwalker on 2013-02-24
The issue with this file is actually quite simple.  in the shell scripts there is a description field and there is a line return then the description.  If the line return could be deleted and the entire package re-assembled into a deb (beyond my ability to do) then the install file should work fine.  Anyone with the knowledge on how to do this?

---

### Post by Mysticwalker on 2013-02-26
ok the error is actually in the control file which is located in the .deb package under the folder DEBIAN.  If someone who knows how to disassemble the package, edit that one file (i.e. remove the cr/lf, aka newline, aka the enter key was pressed, aka I really can't make it any simpler than that) and then re-package it into a .deb file, it should work.  As a side note I have also tried the Lexmark 700 Pro drivers to no avail.  For those who don't know Lexmark manufactures many of Dell's printers.

---

### Post by Mysticwalker on 2013-03-07
If anyone is interested, I have drivers that work.  The Lexmark Pro 715 series drivers work for printing but I cannot get it to scan.  When you install the drivers you must use Lexmark's "Lexmark Printing Utility" to install the printer, and install it via the "ethernet" install only.  After this install goes through you'll print just fine.  Succeeded just now on Ubuntu 12.04. [http://support.lexmark.com/index?locale=EN&page=product&userlocale=EN_US&productCode=LEXMARK_PRO715&focusedTab=DOWNLOADS#2](http://support.lexmark.com/index?locale=EN&page=product&userlocale=EN_US&productCode=LEXMARK_PRO715&focusedTab=DOWNLOADS#2)

---

### Post by cabz on 2013-03-08
> **Mysticwalker said:**
> If anyone is interested, I have drivers that work.  The Lexmark Pro 715 series drivers work for printing but I cannot get it to scan.  When you install the drivers you must use Lexmark's "Lexmark Printing Utility" to install the printer, and install it via the "ethernet" install only.  After this install goes through you'll print just fine.  Succeeded just now on Ubuntu 12.04. [http://support.lexmark.com/index?locale=EN&page=product&userlocale=EN_US&productCode=LEXMARK_PRO715&focusedTab=DOWNLOADS#2](http://support.lexmark.com/index?locale=EN&page=product&userlocale=EN_US&productCode=LEXMARK_PRO715&focusedTab=DOWNLOADS#2)

I tried the link but it wont give linux drivers, did you install the windows drivers with wine? .

---

### Post by cabz on 2013-03-08
> **cabz said:**
> I tried the link but it wont give linux drivers, did you install the windows drivers with wine? .
opps sorry i tried it again and the download link worked this time;)

---

