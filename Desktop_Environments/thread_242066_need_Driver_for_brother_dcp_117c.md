---
title: "need Driver for brother dcp 117c"
date: 2006-08-23
forum: Desktop Environments
---

### Post by rowan369 on 2006-08-23
Is there a driver anywhere fr the brother DCP 117C I have tried brothert website but no joy.

I cannot print tthe printer using drivers supplied with UBUNTU

any suggestions welcome

---

### Post by axel112 on 2007-01-28
Turn your printer off
Download drivers MFC210C - [here you can find them]("http://solutions.brother.com/linux/en_us/index.html")
Install csh with synaptic
Install lpr printerdriver
Install cupswrapperdriver
Turn your printer on
Goto System-Admin-Printing
Add printer Brother117C
Install drivers from ppd-file - location /usr/share/cups/model
Set papersize and, hopefully, you're good to go

---

### Post by orko3001 on 2007-03-12
> Download drivers MFC210C - here you can find them

Can't see the driver on that page...

:confused:

---

### Post by axel112 on 2007-03-13
OK. Here we go then, links below.

[lpr-driver]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc210clpr-1.0.2-1.i386.deb&lang=English_lpr")
[cups-driver]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrappermfc210c_1.0.0-1_i386.deb&lang=English_gpl")
[scanner-driver]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.1-1.i386.deb&lang=English_sane")

Just download them and follow the steps mentioned earlier. Good luck and tell me if you did get it working or not. /axel

---

### Post by orko3001 on 2007-08-31
I found the driver for the scanner:

[http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html)

And tryed to follow the instructions for install here:

[http://solutions.brother.com/linux/sol/printer/linux/sane_install.html](http://solutions.brother.com/linux/sol/printer/linux/sane_install.html)

And got as far as this:


   2. Install the Brother scanner driver

      $ dpkg -i brscan-0.2.3-0.i386.deb
      or
      $ dpkg -i brscan2-0.2.3-0.i386.deb

I had to put sudo as i got dpkg: requested operation requires superuser privilege

But when I did got this:

dpkg: error processing brscan-0.2.3-0.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 brscan-0.2.3-0.i386.deb

So I did sudo apt-get install brscan-0.2.3-0.i386.deb 

But got this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package brscan-0.2.3-0.i386.deb

Key words being "No such file or directory"

Where should I put the file? :confused: I have downloaded it.

Cheers

---

### Post by orko3001 on 2007-08-31
I found this:

>  Re: HOWTO: Install Brother MFC210C
Below are the automated install scripts. It will install the fax, printing and scanner drivers for you. It will also prompt to setup the fax drivers automatically after it installs the drivers. Please note that the setup portion of the fax drivers only prompts if your running gnome. In order to fax, simply right click on any postscript file (ps extenstion) in gnome and select open with BRFAX. The dialer will pop up and you can fax from there. See the first page tutorial for more detailed instructions. Be sure and choose the right version for the OS you are running. If you scanner doesn't work after installing. Try running
Code:

sudo xsane


[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
Here:

[http://ubuntuforums.org/showthread.php?t=105703&page=29](http://ubuntuforums.org/showthread.php?t=105703&page=29)

I did sudo xane and I got a warning saying Install At Your Own Risk - Installing Xsane AS Root Is Really Dangerous..

:confused::confused::confused:

---

