---
title: "dell printer"
date: 2007-08-07
forum: Dell  Ubuntu Support
---

### Post by nofx135 on 2007-08-07
i cant get my dell printer to work at all. My model is Dell A920 and ive tried to add the printer under the administrations menu, it recognizes the printer as Dell A920 (Dell A920 USB #1), after that i click next then it asks for the model but my model # is not listed under the dell section. Can some one please help.

---

### Post by MyR on 2007-08-07
accoring to [http://www.openprinting.org/show_printer.cgi?recnum=Dell-AIO_Printer_A920](http://www.openprinting.org/show_printer.cgi?recnum=Dell-AIO_Printer_A920) it should work perfectly (surprisingly)
use the Lexmark z600 driver

peace

---

### Post by MyR on 2007-08-07
however this person [http://ubuntuforums.org/showthread.php?t=519983](http://ubuntuforums.org/showthread.php?t=519983) seems to be having trouble. so i don't know.

---

### Post by dchriscoe on 2007-08-07
I have a Lexmark Z611 (USB)  that I just installed on Ubuntu 7.04.

It works fine but here is what you have to do:

First I assume that what I have read is correct: that the z600 driver will work with your Dell (equiv to Lexmark 1270).  I downloaded  the z600 package from the Lexmark site. The file CJLZ600LE-CUPS-1.0-1.TAR.gz was placed in my home folder.

Second I had to run Synaptic to install the alien program which converts rpm to deb.  You may already have that program but make sure.

Now the long part, load the terminal and execute in the order below the following :  Note when you "sudo alien" on the two files, ignore the warning messages.


$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz    # extract the package
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz    # put the needed files into a tar file
$ tar -xvzf install.tar.gz     # extract the tar file
$ sudo alien -i z600cups-1.0-1.i386.rpm     # install the printer driver
$ sudo alien -i z600llpddk-2.0-1.i386.rpm    # install misc. printer libraries
$ sudo /etc/init.d/cupsys restart       # restart the cups daemon
$ /usr/lib/cups/backend/z600      # check that the printer backend works (You may get no output here but it works fine)


Go to System - Administration - Printing and choose the printer driver Z600 v1.0-1 under Lexmark (or, if it's not there, go to Install Driver and choose /usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz).

For some resaon I had to install the printer twice. The first time the print driver above was not listed so I did the Install Driver.  The printer did not work so I uninstalled it.  On the second install the printer driver now appeared.  I installed in this way and  it now  prints.

You will  print OK but since the printer manager software for this machine is Windows based, the scan and copy button will probably not work 
__________________

---

