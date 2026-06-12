---
title: "samsung scx 4200: can't share with samba"
date: 2006-06-02
forum: Desktop Environments
---

### Post by suoko on 2006-06-02
Hi,

I followed the instructions for installing scx 4100 multifunction device posted on this forum (reported below). They worked great, although they caused a side problem: now I can't share my printer throught samba anymore.

I guess the problem was caused by the binary driver. Can anyone help me?

How can I debug the problem.
Recap: I can print and scan with the ubuntu pc but I can't print from a window pc in my LAN. The window pc can see the scx4200 printer but then can't print.

I attach my smb.conf, cupsd.conf and printers.conf

thanks

[I]INSTRUCTIONS:

First, you need to install some required libs and programs:

Code:

sudo apt-get install libstdc++2.10-glibc2.2 sudo apt-get install libsane-dev sane sane-utils


Download the updated driver from the SCX-4100 Linux driver download page.
Open a terminal and change to the directory where you downloaded the driver (example: /home/install/samsung_printer):
Code:

cd /home/install/samsung_printer

Extract the driver (the driver could be named something different if it has been updated):
Code:

tar -xzf 20051130084513156_DriversPack-1.0.165.tar.gz

Start the driver installation script:
Code:

sudo ./cdroot/Linux/install.sh

Press "4" because you want to install the "[6] SCX 4100 Series" driver
Press "1" since you want to "[1] Install driver package".
You should already have CUPS installed so Press "2":
[2] I am sure I have necessary software installed. Continue installation
You'll get a whole spew of stuff printed on the screen along with some errors that you can probably just ignore.
Open /etc/cups/printers.conf and change the "DeviceURI" so it looks like this:
Code:

DeviceURI file:/dev/usblp0

Restart cups:
Code:

sudo /etc/init.d/cupsys restart

Printing should now work.
Add 2 lines like this to the end of /etc/udev/rules.d/45-libsane.rules before the LABEL="libsane_rules_end" line (based on output of sane-find-scanner) so that people in the "scanner" group and not only root can use the scanner. (You'll have to reboot after doing this.):
Code:

# Samsung|SCX-4100 SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="3413", MODE="664", GROUP="scanner"


Restart udev:
Code:

sudo /etc/init.d/udev restart

Create a symlink that is required to for Xsane to be able to see the scanner (You'll need to do this every reboot ):
Code:

sudo mkdir /dev/usb sudo ln -sfn /dev/usblp0 /dev/usb/lp0


Scanning using "xsane" and OpenOffice.org (Insert -> Picture -> Scan -> Request) should now work.[/I]

---

### Post by suoko on 2006-06-06
I made it work by removing (through printer-admin) the printer which had been installed by the samsung script and reinstailling it the ubuntu way.

---

### Post by mixandgo on 2006-10-03
I am having problems installing this printer ! are you actually using the 4100 driver instead of the 4200 one ? why is that ? and where are those modules it complains about ?

---

