---
title: "canon lbp-3000"
date: 2006-02-22
forum: Desktop Environments
---

### Post by nrayever on 2006-02-22
hi everyone:

i have a big problem trying to install a printer in a box with breezy. the printer is a canon lbp-3000, and seem impossible to make it work!!

googling in the web, i found some information that this printer is 100% incompatible with linux, but canon website have a linux driver.

[HTML]http://software.canon-europe.com/software/canon_capt_printer_driver_for_linuxs22362.asp?model=[/HTML]

and the drivers has 2 rpm packages. so i tried to install them, so i alienized the packages. the drivers are installed ok, but the is some configuration stuff that i can't figure out how to make it.

this is part of the instrution guide that canon gives with the printer driver.

```
2. Installing/Uninstalling the Printer Driver
Installing the Printer Driver

The printer driver must be installed in order to print from Canon LBP printers using Linux.
The printer driver files to be installed consist of:

    * cndrvcups-capt-1.1X-X.i386.rpm : rpm file of the CAPT printer driver module

    * cndrvcups-common-1.1X-X.i386.rpm : rpm file of a common module for CUPS drivers

Note

    * The files names of the CUPS driver common module and the printer driver module described in this procedure differ depending on the installed driver version. The "1.1X-X" part of the file name indicates the driver version.
    * Before installing this driver, CUPS must be installed and started on the operating system. Also make sure that printers can be added and enabled by various services, according to the security level that has been set.
    * If Canon CAPT Printer Driver for Linux Version 1.01 or later is installed, you can update the existing driver without uninstalling it. For details about updating the printer driver, refer to "Updating the Printer Driver" of "2. Installing/Uninstalling the Printer Driver". However, you cannot update the Version 1.00 printer driver. Refer to "Uninstalling the Printer Driver" of "2. Installing/Uninstalling the Printer Driver" to uninstall the existing printer driver, then install the new printer driver according to the procedure below.
    * To check the version of the printer driver you are using, refer to "Checking the Driver Version" in the "Appendix".
    * You cannot print with this printer driver if LBP-1210 is being used in parallel connection.

1
Start Linux after installation, and log in as 'root'.

$ su
2
Install the common module for CUPS driver.

Enter the following rpm command:

# rpm -ivh cndrvcups-common-1.1X-X.i386.rpm

Note

    * When you execute the rpm command from a directory, specify the path or use the cd command to change the current directory to the directory containing the printer driver files.
    * For details about the rpm command, enter "man rpm" with the terminal software, such as GNOME Terminal. 

3
Install the CAPT printer driver module.

Enter the following rpm command:

# rpm -ivh cndrvcups-capt-1.1X-X.i386.rpm
4
Restart CUPS.

Enter the following command:

# /etc/init.d/cups restart

Note

    * Do not register the printer using the "lpadmin" command before restarting CUPS. 

5
Register the printer (PPD) with the print spooler.

Enter the following command:

# /usr/sbin/lpadmin -p [printer name] -m [PPD file name] -v ccp:/var/ccpd/fifo0 -E

Example: To register the LBP3200 in the print spooler as "LBP3200":

# /usr/sbin/lpadmin -p LBP3200 -m CNCUPSLBP3200CAPTK.PPD -v ccp:/var/ccpd/fifo0 -E

Note

    * For the PPD file corresponding to your printer, refer to "Supported Canon Products" of "1. Introduction". 

6
Register the printer in the ccpd daemon setup file.

Enter the following command.

# /usr/sbin/ccpdadmin -p [printer name] -o [printer device path]

Example: Register LBP3200 in the ccpd daemon setup file.

# /usr/sbin/ccpdadmin -p LBP3200 -o /dev/usb/lp0
7
Start ccpd daemon.

Enter the following command.

# /etc/init.d/ccpd start

Note

    * It would be convenient to set ccpd daemon to start automatically when Linux starts up. 


```

and on steps 6 and 7, when i try to run those commands an error is displayed. when i try to send a print job to the printer the status is "printing" but nothing happends. is there any way to solve this problem?? any soltion that isn't changing the printer?? i hope someone could help me

sincerly nrayever

---

### Post by mkuutti on 2006-06-15
This seems very odd problem. I bought also LBP-2900 because there was linux driver available and now consider it as bad investment :-( 

I've spent several evenings to debianize capt-drivers, I tried instructions from french site:
[http://doc.ubuntu-fr.org/materiel/imprimante_canon_lbp_3200]("http://doc.ubuntu-fr.org/materiel/imprimante_canon_lbp_3200")

Next thing to do was extract sources from src.rpm packages and compile drivers for Dapper, which lead to fixing code and finally it was worth nothing because i found that these "so-called GPL'ed" drivers have several binary files which have no source code available. 

Anyway, with those french instructions i was able to create CUPS printer and correct fifos and start ccpd etc. KDE printer manager showed printer ok, but when tried to print, printing process stucked until removed from queue and killed subprocesses. I guess it was some of those binary filters which stopped.

Next thing to do, should be stracing those binary files to find out what's going on there. I think it will be easier to install FC-4 to some old box for printer server than tracing canon's binaries..

Anyway, I'm VERY disappointed to Canon's way to publish drivers, sources are not all sources, and source code does not use autotools and normal Makefile syntax (for dh_make). I'm wondering what do they lose if they open-source drivers completely? Well, Ubuntu seems to be "hottest" distribution (by distrowatch) so they'll lose lots of linux users at least. Now I should propably re-install my Windows(spoiled by worms) installation to get printing support. It'll be fun, last time XP(even SP-2 enabled media) didn't recognize my sata-controller (but did load correct driver) and I had to install floppy drive to install. Next mistake was that I had my network plugged while installing, system was compromised before SP-2 was installed. My advice for Windows installation: Download ALL stuff (servicepacks, antivirus, drivers) using Linux and burn 'em to cd before installing anything and unplug all network cables during installation.

---

### Post by azray on 2006-06-15
I had a simular problem with a Canon mps390. My solution was to download a program called turboprint at this site   [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

Try thr trial and see if ti works first

---

### Post by nrayever on 2006-06-23
[QUOTE=mkuutti]This seems very odd problem. I bought also LBP-2900 because there was linux driver available and now consider it as bad investment :-( [/QUOTE]

welcome to the club my friend!!

> Anyway, I'm VERY disappointed to Canon's way to publish drivers, sources are not all sources, and source code does not use autotools and normal Makefile syntax (for dh_make). I'm wondering what do they lose if they open-source drivers completely? Well, Ubuntu seems to be "hottest" distribution (by distrowatch) so they'll lose lots of linux users at least. Now I should propably re-install my Windows(spoiled by worms) installation to get printing support. It'll be fun, last time XP(even SP-2 enabled media) didn't recognize my sata-controller (but did load correct driver) and I had to install floppy drive to install. Next mistake was that I had my network plugged while installing, system was compromised before SP-2 was installed. My advice for Windows installation: Download ALL stuff (servicepacks, antivirus, drivers) using Linux and burn 'em to cd before installing anything and unplug all network cables during installation.

the real problem is with canon, the don't have a specialized area for linux drivers. they still don't consider linux as big as micro$oft. maybe we should start an online petition to canon for better linux drivers.

the printer that's making me sick, is at my brother's office. actualy the printer is working in a winxp computer. and even for windows the driver was hard to install. canon printers are so bad that even with printer-server the wouldn't work!

so when my brother's boss asked my for a printer, i suggested him a hp printer. hope someday canon printers work good on any linux distro.

[QUOTE=azray]I had a simular problem with a Canon mps390. My solution was to download a program called turboprint at this site   [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

Try thr trial and see if ti works first[/QUOTE]

thanks for the tip azray, but seems that the printer is not on the supported printers list. ](*,) ](*,)

---

### Post by krokodil on 2006-08-08
Will probably also work for the LBP 3000:

[http://www.ubuntuforums.org/showthread.php?p=1356211](http://www.ubuntuforums.org/showthread.php?p=1356211)

---

### Post by mauro on 2006-10-14
:) :) 
I just had to follow this [instructions]("https://wiki.ubuntu.com/Canon_LBP_2900_HowTo") to had success in installing an LBP 3000 printer.

---

### Post by Linux O)o_O7 on 2006-11-04
I tried it 3x and it fails for me.

I have a LBP 300 but it says it should still work. ](*,) 




Does this help? Where am I going wrong?


owner@Linux-Performance:~$ sudo alien -c cndrvcups-capt-1.30-1.i386.rpm
mkdir: cannot create directory `cndrvcups-capt-1.30': File exists
mkdir: cannot create directory `cndrvcups-capt-1.30/debian': File exists
cndrvcups-capt_1.30-2_i386.deb generated
owner@Linux-Performance:~$ sudo alien -c cndrvcups-common-1.30-1.i386.rpm
cndrvcups-common_1.30-2_i386.deb generated
owner@Linux-Performance:~$ sudo dpkg -i cndrvcups-common_1.30-2_i386.deb cndrvcups-capt_1.30-2_i386.deb
Selecting previously deselected package cndrvcups-common.
(Reading database ... 93986 files and directories currently installed.)
Unpacking cndrvcups-common (from cndrvcups-common_1.30-2_i386.deb) ...
Selecting previously deselected package cndrvcups-capt.
Unpacking cndrvcups-capt (from cndrvcups-capt_1.30-2_i386.deb) ...
Setting up cndrvcups-common (1.30-2) ...

Setting up cndrvcups-capt (1.30-2) ...

owner@Linux-Performance:~$ sudo /etc/init.d/cupsys stop
 * Stopping Common Unix Printing System: cupsd                           [ ok ] 
owner@Linux-Performance:~$ sudo ps ax | grep cupsd
20198 pts/0    R+     0:00 grep cupsd
owner@Linux-Performance:~$ sudo /etc/init.d/cupsys start
 * Starting Common Unix Printing System: cupsd                           [ ok ] 
owner@Linux-Performance:~$ sudo mkdir /var/ccpd
mkdir: cannot create directory `/var/ccpd': File exists
owner@Linux-Performance:~$ sudo mkdir /var/captmon
mkdir: cannot create directory `/var/captmon': File exists
owner@Linux-Performance:~$ sudo mkfifo /var/ccpd/fifo0
mkfifo: cannot create fifo `/var/ccpd/fifo0': File exists
owner@Linux-Performance:~$ sudo chmod 777 /var/ccpd/fifo0
owner@Linux-Performance:~$ sudo /usr/sbin/lpadmin -p [LBP3000] -m [printer driver file] -v ccp:/var/ccpd/fifo0 -E
lpadmin: Unable to copy PPD file!
owner@Linux-Performance:~$ ls /usr/share/cups/model/ | grep CNCUPS
CNCUPSLBP1120CAPTJ.ppd
CNCUPSLBP1120CAPTK.ppd
CNCUPSLBP1210CAPTJ.ppd
CNCUPSLBP1210CAPTK.ppd
CNCUPSLBP2900CAPTK.ppd
CNCUPSLBP3000CAPTJ.ppd
CNCUPSLBP3000CAPTK.ppd
CNCUPSLBP3200CAPTJ.ppd
CNCUPSLBP3200CAPTK.ppd
CNCUPSLBP3210CAPTJ.ppd
CNCUPSLBP3210CAPTK.ppd
CNCUPSLBP3300CAPTJ.ppd
CNCUPSLBP3300CAPTK.ppd
CNCUPSLBP3600CAPTJ.ppd
CNCUPSLBP5000CAPTJ.ppd
CNCUPSLBP5000CAPTK.ppd
owner@Linux-Performance:~$ sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP3000CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
lpadmin: Unable to copy PPD file!
owner@Linux-Performance:~$ sudo /usr/sbin/lpadmin -p LBP3000 -m CNCUPSLBP3000CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
lpadmin: Unable to copy PPD file!
owner@Linux-Performance:~$ sudo /usr/sbin/lpadmin -p LBP3000 -m CNCUPSLBP3000CAPTJ.ppd -v ccp:/var/ccpd/fifo0 -E
lpadmin: Unable to copy PPD file!
owner@Linux-Performance:~$ sudo /usr/sbin/ccpdadmin -p LBP2300 -o /dev/usblp0

 LBP2300 can't find in CUPS Spooler Entry!!

owner@Linux-Performance:~$

---

### Post by Linux O)o_O7 on 2006-11-04
I am fairly new to Linux OS (I first tried over a year ago after wanting to for so long) but have tried all the major ones and I like ubuntu best right now.

If only this printer driver was made for ubuntu then I would only have to click install.

All I need for my ubuntu is web design software, media burning software, office software and all basic essentials. 

I am just an end user that is all - well a power user ;)

Hopefully one of you can help me solve this.

---

### Post by djXpire on 2007-01-26
> **mauro said:**
> :) :) 
I just had to follow this [instructions]("https://wiki.ubuntu.com/Canon_LBP_2900_HowTo") to had success in installing an LBP 3000 printer.

My printer is LBP5000, reading through most of the links found on Google, installation should work the same as LBP 
2900 or LBP3000...

And I've followed the instruction from your given link found on Google but I am stuck at the following step:

[IMG]http://img154.imageshack.us/img154/5265/screenshotdjxpiredjibmlkl7.png[/IMG]

Though from the guide, it stated that "In Ubuntu Edgy, change the owner of fifo0 into root (failing to do so gives you an error: Unable to copy PPD file in step 4):" but seems like I couldn't get it to work...

Actually I am trying to get the LBP5000 to be installed via the MS Network, I tried sharing the printer using SMB method but couldn't work as well.... 

Anyone can guide me along on making the MS networked LBP5000 to work on my Edgy...  thanks a lot! :D

---

### Post by crgutierrez on 2007-04-14
> **mauro said:**
> :) :) 
I just had to follow this [instructions]("https://wiki.ubuntu.com/Canon_LBP_2900_HowTo") to had success in installing an LBP 3000 printer.

It works with lbp3000!! Thank you, but it also uses 100% of the CPU and is veeeerrrrryyyyy slllooooow. how can I reduce the use of the CPU????

---

### Post by mauro on 2007-05-06
Try:
sudo /usr/sbin/lpadmin -p LBP3000 -p CNCUPSLBP3000CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
This way worked here.

---

### Post by Jellus on 2007-05-26
There is a new driver for LBP-3000 available .. the weird thing is that it is only available on canon's australian website .. maybe we should sent them an email to change this .. worldwide ...

Here is the link ...

[http://www.canon.com.au/products/printers/laser_printers_low_medium_volume/lbp3000_support.aspx](http://www.canon.com.au/products/printers/laser_printers_low_medium_volume/lbp3000_support.aspx)

Click driver downloads then you go here:

[http://alpha02.c-wss.com/inc/ApplServlet?SV=WWUCA900](http://alpha02.c-wss.com/inc/ApplServlet?SV=WWUCA900)

Next you get to select a driver from the list below:

    Drivers
         Canon Advanced Printing Technology for Canon LBP3000 R1.10 Windows 2000/XP/Server 2003/Vista
	
         Canon Advanced Printing Technology for Canon LBP3000 R1.03 Windows 2000
	
         Canon Advanced Printing Technology for Canon LBP3000 R1.03 Windows 98_Me
	
         Linux Printer Driver(CAPT) Ver.1.50E

Notice the new driver ...

By the way my experience is that these drivers work best with USB2.0 ports ... USB1.1 doesnt work so well with usb printers .. imhxp

You can download two archives one for the driver and another for the source ...

CAPT_Printer_Driver_for_Linux_V1.50E(6.18MB)
CAPT_Printer_Driver_for_Linux_Driver150[1].tar.gz

CAPT_Printer_Driver_for_Linux_source file_V150E(4.60MB)
CAPT_Printer_Driver_for_Linux_Src150[1].tar.gz 

Setting up of the new driver is explained in the readme ... as usual ...

One thank you is in order for Canon Australia i would say .. from my linux heart ...

Thanx Canon Australia .. as this driver seems to work very good on linux ...

Cheers

Jelle Wierdsma

---

### Post by Jellus on 2007-05-26
The printer driver must be installed in order to print from Canon printers using Linux.
The installed files differ depending on the system environment you are using.

In a Debian environment, install the following files:

    * "cndrvcups-common_x.xx-x_i386.deb" : common module for CUPS drivers

    * "cndrvcups-capt_x.xx-x_i386.deb" : CAPT printer driver module

Note

    * The version of each module is indicated as "x.xx-x".
    * Before installing this driver, CUPS must be installed and started on the operating system. Also make sure that printers can be added and enabled by various services, according to the security level that has been set.
    * Because this printer driver uses the CAPT filter, Ghostscript needs to be installed and updated according to the system environment. Obtain a Ghostscript module from the website of each operating system's distributor in advance, according to the system environment.
    * If Canon CAPT Printer Driver for Linux Version 1.01 or later is installed, you can update the existing driver without uninstalling it. For details about updating the printer driver, refer to "Updating the Printer Driver" of "2. Installing/Uninstalling the Printer Driver".
    * To check the version of the printer driver you are using, refer to "Checking the Driver Version" in the "Appendix".
    * You cannot print with this printer driver if LBP-1210 is being used in parallel connection.
    * If you want to use LBP5300/3500/3300/5000 on a network, you need to set the IP address for the network board before installing the printer driver. For details on setting the IP address for the network board, see "Specifying the IP Address for the Network Board" in "Appendix".

1
Start Linux after installation, and log in as 'root'.

$ su
2
Install the common module for CUPS driver.

Enter the following rpm command:

# sudo dpkg -i cndrvcups-common_x.xx-x_i386.deb

you will notice when doing this that lots of libs are missing ...

sudo dpkg -i cndrvcups-common_1.50-1_i386.deb
Selecting previously deselected package cndrvcups-common.
(Reading database ... 88059 files and directories currently installed.)
Unpacking cndrvcups-common (from cndrvcups-common_1.50-1_i386.deb) ...
dpkg: dependency problems prevent configuration of cndrvcups-common:
 cndrvcups-common depends on libcupsys2-gnutls10 (>= 1.1.23-1); however:
  Package libcupsys2-gnutls10 is not installed.
 cndrvcups-common depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 cndrvcups-common depends on libgtk1.2 (>= 1.2.10-4); however:
  Package libgtk1.2 is not installed.
dpkg: error processing cndrvcups-common (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cndrvcups-common

The libs libgtk1.2 and libglib1.2 are easily installed on ubuntu feisty .. as it provides these libs still ... 

one lib ubuntu feisty doesnt have available ... is a dummy lib called: "libcupsys2-gnutls10" that was needed for transition to libcupsys2 .. the new driver from canon however still asks for it .. dapper is the last ubuntu version to have that dummy lib ... it is possible to install this dummy lib on feisty though ... the only dependency for it is libcupsys ... perhaps it is ok for it to depend on a newer libcupsys without recompiling it for feisty ...

here it is:

[http://librarian.launchpad.net/3739488/libcupsys2-gnutls10_1.2.2-0ubuntu0.6.06_all.deb](http://librarian.launchpad.net/3739488/libcupsys2-gnutls10_1.2.2-0ubuntu0.6.06_all.deb)

so i installed to see if this will work on feisty ... probably works good on dapper for sure ...

Note

    * When you execute the rpm command from a directory, specify the path or use the cd command to change the current directory to the directory containing the printer driver files.
    * For details about the rpm command, enter "man rpm" with the terminal software, such as GNOME Terminal. 

3
Install the CAPT printer driver module.

Enter the following rpm command:

# sudo dpkg -i cndrvcups-capt_x.xx-x_i386.deb

4
Restart CUPS.

Enter the following command:

# sudo /etc/init.d/cupsys restart


Note

    * Do not register the printer using the "lpadmin" command before restarting CUPS. 

5
Register the printer (PPD) with the print spooler.

Enter the following command:

# /usr/sbin/lpadmin -p [printer name] -p [PPD file name] -v ccp:/var/ccpd/fifo0 -E

Example: To register the LBP3000 in the print spooler as "LBP3000":

cd /usr/share/cups/model

sudo /usr/sbin/lpadmin -p LBP3000 -P CNCUPSLBP3000CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E 

Note

    * For the PPD file corresponding to your printer, refer to "Supported Canon Products" of "1. Introduction". 

6
Register the printer in the ccpd daemon setup file.

USB Connection

Enter the following rpm command:

# /usr/sbin/ccpdadmin -p [Printer Name] -o [Printer Device Path]

Example: To register LBP3000 in the ccpd daemon setup file:

sudo /usr/sbin/ccpdadmin -p LBP3000 -o /dev/usb/lp0

7
Start ccpd daemon.

Enter the following command.

# sudo /etc/init.d/ccpd start

Note

    * It would be convenient to set ccpd daemon to start automatically when Linux starts up. 

Auto startup setting procedure for ccpd daemon -------------------------------
When setting the Status Monitor to start automatically, ccpd daemon must be set
to start automatically as well.
Set ccpd daemon to start automatically in the following procedure.

<For a distribution with a /etc/rc.local file>
Log in as 'root' and add the '/etc/init.d/ccpd start' command to the
/etc/rc.local file.

This is all for now ... testing it it works for me now  ... after reboot ...

---

### Post by Jellus on 2007-05-27
Hi again,

cant seem to be able to get it to work on ubuntu feisty .. quite a shame as ubuntu rocks for the rest ..
maybe some developer can create a dummy lib ..  libcupsys2-gnutls10 .. that works .. for .. ubuntu feisty .. with this new driver .. i can tell you .. the new driver works perfectly on fedora core 7 .. so for lbp3000 owners .. if you cant get your driver to work with ubuntu .. try fedora .. by the way .. neither fedora nor ubuntu is necessarily better than the other ... i like both myself ... although fedora works better for me now ...

Maybe some ubuntu devs can work this out for us all ...  its a shame it doesnt work on ubuntu .. it might work on debian though .. cant say as i didnt test this ... it would seem more logical for canon to release drivers for a current ubuntu though .. as its more popular ... and is being installed on dell hardware nowadays which is way cool btw ...

Cheers,

Jellus

---

### Post by dryder on 2007-06-05
> maybe some developer can create a dummy lib .. libcupsys2-gnutls10 .. that works .. for .. ubuntu feisty .. with this new driver .. i can tell you .. the new driver works perfectly on fedora core 7

Has anybody found a solution to this yet for the Aussie driver?

Jellus, your steps are very welcome for the lbp3000 but dare I say a little daunting for the less experienced?

Would you be prepared to do it in a simplified step by step form? For example, as I understand it CUPS is installed on Ubuntu Edgy and Feisty (at least) - isn't that how Ubuntu printers are installed, via CUPS?

David

---

### Post by dryder on 2007-06-18
I followed the installation procedure using the dummy libcupsys2-gnutls10.

sudo ccpdadmin gives me:
Usage: 
  ccpdadmin [-p Printer-name -o Printer-dev-path]
  ccpdadmin [-x Remove-Printer-name]


 CUPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 59787

 Entry Num  : Spooler   : Backend       : FIFO path             : Device Path  : Status 
 ----------------------------------------------------------------------------
     [0]    : LBP3000   : usb           : //Canon/LBP3000       : /dev/usb/lp0 :



But captstatusui -P LBP3000 gives me :
Printer Error
Check the DevicePath of /etc/ccpd.conf

The DevicePath in /etc/ccpd.conf is:
<Printer LBP3000>
DevicePath /dev/usb/lp0
</Printer>

Is there something I need to / can check to make sure the settings are correct?

Thanks
David

---

### Post by Jellus on 2007-06-24
Hi dryder i managed to make it work now ...

My method is based in part on:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

Now for my method:

Step 1: Get the new driver

[http://www.canon.com.au/products/pri...0_support.aspx](http://www.canon.com.au/products/pri...0_support.aspx)

Click driver downloads then you go here:

[http://alpha02.c-wss.com/inc/ApplServlet?SV=WWUCA900](http://alpha02.c-wss.com/inc/ApplServlet?SV=WWUCA900)

Next you get to select a driver from the list below:

Drivers
Canon Advanced Printing Technology for Canon LBP3000 R1.10 Windows 2000/XP/Server 2003/Vista

Canon Advanced Printing Technology for Canon LBP3000 R1.03 Windows 2000

Canon Advanced Printing Technology for Canon LBP3000 R1.03 Windows 98_Me

Linux Printer Driver(CAPT) Ver.1.50E

Notice the new driver ...

By the way my experience is that these drivers work best with USB2.0 ports ... USB1.1 doesnt work so well with usb printers .. imhxp

You can download two archives one for the driver and another for the source ...

CAPT_Printer_Driver_for_Linux_V1.50E(6.18MB)
CAPT_Printer_Driver_for_Linux_Driver150[1].tar.gz

CAPT_Printer_Driver_for_Linux_source file_V150E(4.60MB)
CAPT_Printer_Driver_for_Linux_Src150[1].tar.gz

Setting up of the new driver is explained in the readme ... as usual ...

Step 2: installing prerequisites (deps) and the binary canon driver packages

Download libcupsys-gnutls10 from a Dapper repository (Edgy and Feisty and later dont have it in their repositories !) which is a dummy lib needed for transition to libcupsys2.
The new driver from Canon didnt make the transition to libcupsys2 yet and so still depends on it.

Download the driver from:

[http://za.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2-gnutls10_1.2.0-0ubuntu5_all.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2-gnutls10_1.2.0-0ubuntu5_all.deb)

After downloading install it as follows:

$ sudo dpkg -i libcupsys2-gnutls10_1.2.0-0ubuntu5_all.deb

Then install some other deps which are needed by the binary (sadly not everything is open source with these canon drivers :( ) canon driver packages cndrvcups-common and cndrvcups-capt as follows:

$ sudo aptitude install libglib1.2 libgtk1.2

After satisfying these deps in ubuntu feisty (32-bit) install the binary canon driver packages themselves:

$ sudo dpkg -i cndrvcups-common_1.50-1_i386.deb cndrvcups-capt_1.50-1_i386.deb

Step 3:

In order to load the new drivers we have installed we need to stop and restart CUPS. Firstly we stop CUPS:

$ sudo /etc/init.d/cupsys stop

Check that it is stopped. All the times I have done this, CUPS had stopped first time but apparently this may not always be the case due to the installation of ccp:

$ sudo ps ax | grep cupsd

Which will give you something like this:

cupsys   24897  0.0  0.1   4336  1976 ?        SNs  07:35   0:04 /usr/sbin/cupsd
username 24738  0.0  0.0   2896   836 pts/0    S+   21:21   0:00 grep cupsd

If you only get a line that ends with "grep cupsd" CUPS has stopped and you can carry on. If you also get a line that ends with "/usr/sbin/cupsd", as shown above, CUPS has not stopped and you will have to try the following method to stop it:

$ sudo killall cupsd

The debs are not perfect so we have to do some extra work to make it work.

Make fifo0 accessable to everyone:

$ sudo chmod 777 /var/ccpd/fifo0

Change the owner of fifo0 into root (failing to do so gives you an error: Unable to copy PPD file in step 4):

$ sudo chown root /var/ccpd/fifo0

Once you have done this, start CUPS again:

$ sudo /etc/init.d/cupsys start

Step 4:

Register the printer driver with the print spooler with the following command, replacing [printer model] with your printer model and [printer driver file] with your driver file:

$ sudo /usr/sbin/lpadmin -p [printer model] -P [printer driver file] -v ccp:/var/ccpd/fifo0 -E

For example, the command for the Canon LBP 3000 would be:

$ sudo /usr/sbin/lpadmin -p LBP3000 -P CNCUPSLBP3000CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E

If you are unsure of what your driver file is called you can get a list of the available drivers:

$ ls /usr/share/cups/model/ | grep CNCUPS

Look for the one that matches your model number. Some of them end with "K.ppd" and some end with "J.ppd". I have no idea what difference is, the K ones have worked fine for me so far.

Ubuntu Feisty is searching the for driver in /usr/share/ppd/ so I created a link:

$ cd /usr/share/ppd/
$ sudo ln -s /usr/share/cups/model/CNCUPSLBP3000CAPTK.ppd

Once registered your printer should appear in the System > Administration > Printing dialog.

Register the printer with ccpd daemon, once again replace [printer model] with your printer model:

$ sudo /usr/sbin/ccpdadmin -p [printer model] -o /dev/usblp0

For example, the command for the Canon LBP 3000 would be:

$ sudo /usr/sbin/ccpdadmin -p LBP3000 -o /dev/usblp0

if it complains about file not found .. do it like this:

$ cd /usr/share/cups/model

and repeat the other statement

$ sudo /usr/sbin/ccpdadmin -p LBP3000 -o /dev/usblp0

it should work now ..

Step 5:

Replace /etc/init.d/ccpd with the script below:

#!/bin/sh
#
# ccpd          startup script for Canon Printer Daemon for CUPS
#
#               Modified for Debian GNU/Linux
#               by Raphael Doursenaud <rdoursenaud@free.fr>.

DAEMON=/usr/sbin/ccpd
LOCKFILE=/var/lock/subsys/ccpd
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME=ccpd
DESC="Canon Printer Daemon for CUPS"

test -f $DAEMON || exit 0

case $1 in
  start)
        echo -n "Starting $DESC: $NAME"
        start-stop-daemon --start --quiet --exec $DAEMON
        echo "."
        ;;
  stop)
        echo -n "Stopping $DESC: $NAME"
        start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
        echo "."
        ;;
  status)
        echo "$DESC: $NAME:" `pidof $NAME`
        ;;
  restart)
        echo -n "Restarting $DESC: $NAME"
        start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
        sleep 1
        start-stop-daemon --start --quiet --exec $DAEMON
        echo "."
        ;;
  *)
        echo "Usage: ccpd {start|stop|status}"
        exit 1
        ;;
esac

exit 0

Copy and paste the above script into a new text file, then backup and replace the old version:

$ sudo mv /etc/init.d/ccpd ccpdold
$ sudo cp [text file you created] /etc/init.d/ccpd

Give everyone execution rights to the new file:

$ sudo chmod a+x /etc/init.d/ccpd

Step 6:

Start the ccpd daemon:

$ sudo /etc/init.d/ccpd start

Step 7:

Set ccpd to start when you startup your computer:

$ sudo update-rc.d ccpd defaults 20

Step 8:

Switch off the printer and reboot your computer. Once you have logged in, switch on the printer again.

Step 9:

Test your installation (Don't forget to switch on your printer after logging in).

First test:

$ sudo ccpdadmin

Which should output this:

Usage:
  ccpdadmin [-p Printer-name -o Printer-dev-path]
  ccpdadmin [-x Remove-Printer-name]


 CUPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 39787

 Entry Num  : Spooler   : Backend       : FIFO path             : Device Path  : Status
 ----------------------------------------------------------------------------
     [0]    : LBP3000   : ccp           : /var/ccpd/fifo0       : /dev/usblp0  :

Second test, replace [printer model] with your printer model

$ captstatusui -P [printer model]

For example, the command for the Canon LBP 3000 would be:

$ captstatusui -P LBP3000

This will launch a window that after a bit should say "ready to print".

Finally open a file and try to print it. 

And it works .. this is in no way encouragement to Canon to keep their drivers closed source partly though ... :) .. i am just glad i dont have to throw my new canon laserprinter away ...

Ok good luck dryder .. i hope this will work for you too .... :)

For now ...

Cheers Jellus ...

---

### Post by dryder on 2007-06-24
Hi Jellus,

Thanks for this I'll certainly give it a try - will let you know but may be a few days til I get the chance due to the storms we had.

David

---

### Post by dryder on 2007-06-24
> Set ccpd to start when you startup your computer:

$ sudo update-rc.d ccpd defaults 20

I have read the documentation - but found nothing to answer this:

What is the command to _stop_ ccpd starting at startup, please?

---

### Post by dryder on 2007-06-24
Apologies (Jellus et al) for making three consecutive posts ...

I don't see the need to download the source code from the Aussie Canon site as it does not appear that you use it. Am I missing something? Is it just for distros that need the driver modifying?

I rang Canon Australia (extremely nice and helpful people) - only problem was nobody in tech support knew there even was a linux driver on the site! :D

---

### Post by Jellus on 2007-06-26
Hi dryder,

No you only need to download the binary drivers from canon australia .. not the source .. the source is useless imho ... at least the sources they are providing at the moment .. with all respect for the canon australia people .. it is good to hear they are friendly and helpful .. thats always welcome imho ...

I checked my url's that i posted earlier .. it seems like the website was updated ... i used this url now .. to see where the drivers are ...

[http://www.canon.com.au/products/printers/laser_printers_low_medium_volume/lbp3000_support.aspx](http://www.canon.com.au/products/printers/laser_printers_low_medium_volume/lbp3000_support.aspx)

click on driver downloads ...

next click on Linux Printer Driver (CAPT) Ver. 1.50E

next scroll down from the software license to where you can download the source and the binaries seperately ..

Below is listed what you need to download for the binaries ... i mean the tarball off course :)

CAPT_Printer_Driver_for_Linux_V1.50E(6.18MB)

CAPT_Printer_Driver_for_Linux_Driver150[1].tar.gz 

Click on the tarball containing the binaries .. which is the one above and download it ...

after downloading unpack it ..

when it is unpacked .. go into the CAPT_Printer_Driver_for_Linux_Driver150 directory ... and below that dir there are two directories .. to be more specific .. Doc and Driver .. go into the Driver directory ... in that directory .. there are again two directories .. now they are called Debian and RPM .. go into the Debian directory .. there you will find both .deb packages needed for installation ...

As to your other question i will have to come back on that .. i dont know this by heart either .. honestly i didnt feel the need yet to stop ccpd from starting up everytime ... by the way .. it is a good habit to start up the status app too everytime .. you start up too ... as you need this status app sometimes to tell the printer to print .. at least from the status app you have a clue why the printer wont print if it is not printing .. i experienced one time .. that it wouldnt print .. cause it needed new paper .. it said .. but it was there .. so i told it to resume printing with the status app ... and then it simply prints ... it works like a charm ...

Canon should put some more energy into keeping their drivers up to date though imho .. although i am glad i was able to make it work ... now ... this is only meant as constructive criticism .. for canon ... i wish canon would do even more .. i would applaud it .. linux rocks .. vista sucks ... better develop for a cool os instead of for a dead fish in the water .. with all due respect for M$ winblows vista .. :)

Cheers,

Jellus

---

### Post by Jellus on 2007-06-26
Lol in a way it is funny they didnt know about their linux drivers ... in another way .. this is a signal that canon needs to spend more time and money on linux drivers in general .. and make their workers aware of the drivers they are creating ... just something i couldnt help saying ... :) .. fun to hear from you though ... i guess we all come accross this sooner or later .. i hope this will change soon as linux is getting more mainstream ... at work as well ... which would be a good thing .. imho .. 

Cheers,

Jellus

---

### Post by dryder on 2007-06-26
> by the way .. it is a good habit to start up the status app too every time .. you start up too ... as you need this status app sometimes to tell the printer to print

Aha - so that's why I don't get a status monitor ! :-)

Presumably I start it via System>Preferences>Sessions .. ?

I agree re the linux driver but did it originate in Australia? If not then why isn't it on other Canon sites? I had though _perhaps_ there was a linux user in Canon Australia who wrote it ... just a thought ..
David

---

### Post by Jellus on 2007-06-27
Hi dryder,

On other canon sites you can find an older driver it seems .. version 1.3 ... as this driver is newer i wanted to try out this one ... why it isnt the same worldwide i dont have a clue ... the origin of the driver i dont know exactly .. but take a look here ....

[http://www.linux-foundation.org/images/9/9b/2006-10-23-Linux_Printer_Drivers_from_Canon_061022-1.pdf](http://www.linux-foundation.org/images/9/9b/2006-10-23-Linux_Printer_Drivers_from_Canon_061022-1.pdf)

It seems that the driver was originally developed for the japanese market .. open source will be very strong in the asian world ... i think ... and they put a lot of effort into it there i know .. you can read about this a lot .. turbolinux is a known japanese distro

It is a good idea to create a launcher on your desktop with as command ... captstatusui -P LBP3000
you can run this from cli as well off course .. i made this launcher for myself as its a lot easier this way ...

Ok i hope this helps you out ... a bit more ..

Cheers,

Jellus

---

### Post by dryder on 2007-07-06
Hi,

Playing with feisty 64 bit I note the canon driver gives an error "wrong architecture".

Is there a way to convert (the Canon) 32 bit drivers to 64 bit? i notice in the source driver download there is a folder "libsx86_64"

David

---

### Post by Jellus on 2007-07-26
Hi dryder,

We still live more or less in a 32-bit world .. cpus are capable of running 32-bit os's .. as long as most not totally open source drivers are not made compatible with 64-bit os stick to a 32-bit os .. you can run 32-bit ubuntu on a 64-bit cpu .. that is if you have a good one like an amd cpu ..

Cheers,

Jellus

---

### Post by Velosiped on 2007-11-04
> **Jellus said:**
> 
Second test, replace [printer model] with your printer model

$ captstatusui -P [printer model]

For example, the command for the Canon LBP 3000 would be:

$ captstatusui -P LBP3000

This will launch a window that after a bit should say "ready to print".

Finally open a file and try to print it. 

And it works .. this is in no way encouragement to Canon to keep their drivers closed source partly though ... :) .. i am just glad i dont have to throw my new canon laserprinter away ...

Ok good luck dryder .. i hope this will work for you too .... :)

For now ...

Cheers Jellus ...

Hi 

I am instaling LBP3200 right now and everything seemed to be fine since the second test  in step 8. Here is the answer I got in terminal:

"administraator@ubuntu:~$ captstatusui -P LBP3200
captstatusui: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory"

What's wrong with it?

---

### Post by zardosht on 2007-12-30
just install libgtk-1.2 under synaptic

it worked for me.

---

### Post by suoko on 2008-02-03
has anyone tried with new captdrv160.tar.gz ?
I'm trying the included debs with no success

---

### Post by pmorton on 2008-03-04
re: "has anyone tried with new captdrv160.tar.gz ?"

I got the LBP5000 (no different from  the LBP3000)  working with Hardy by following Jellus' excellent post (repeated below in my own summary).
 Found tip on French Ubuntu forum to switch printer on BEFORE rebooting. That solved my problem. Now works fine.


Canon LBP5000 Driver Installation
sudo dpkg -i ~/Desktop/LBP5000/cndrvcups-common_1.60-1_i386.deb
sudo dpkg -i ~/Desktop/LBP5000/cndrvcups-capt_1.60-1_i386.deb
sudo /etc/init.d/cupsys stop
sudo ps ax | grep cupsd
(should show a line with grep cupsd at the end, showing its stopped)
sudo chmod 777 /var/ccpd/fifo0
sudo chown root /var/ccpd/fifo0
sudo /etc/init.d/cupsys start
sudo /usr/sbin/lpadmin -p LBP5000 -P /usr/share/cups/model/CNCUPSLBP5000CAPTK.ppd  -v ccp:/var/ccpd/fifo0 -E
cd /usr/share/ppd
sudo ln -s /usr/share/cups/model/CNCUPSLBP5000CAPTK.ppd
Printer should appear in System > Administration > Printing
sudo /usr/sbin/ccpdadmin -p LBP5000 -o /dev/usb/lp0
sudo gedit /etc/init.d/ccpd
and replace text with the following bash script:

		#!/bin/sh
		# ccpd startup script for Canon Printer Daemon for CUPS
		# Modified for Debian GNU/Linux
		# by Raphael Doursenaud <rdoursenaud@free.fr>.
		DAEMON=/usr/sbin/ccpd
		LOCKFILE=/var/lock/subsys/ccpd
		PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/us r/sbin:/usr/bin
		NAME=ccpd
		DESC="Canon Printer Daemon for CUPS"
		test -f $DAEMON || exit 0
		case $1 in
		start)
		echo -n "Starting $DESC: $NAME"
		start-stop-daemon --start --quiet --exec $DAEMON
		echo "."
		;;
		stop)
		echo -n "Stopping $DESC: $NAME"
		start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
		echo "."
		;;
		status)
		echo "$DESC: $NAME:" `pidof $NAME`
		;;
		restart)
		echo -n "Restarting $DESC: $NAME"
		start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
		sleep 1
		start-stop-daemon --start --quiet --exec $DAEMON
		echo "."
		;;
		*)
		echo "Usage: ccpd {start|stop|status}"
		exit 1
		;;
		esac
		exit 0

sudo chmod a+x /etc/init.d/ccpd 
sudo /etc/init.d/ccpd start
sudo gedit /etc/rc.local
and add the line: " /etc/init.d/ccpd start "
Switch off printer, switch back on, THEN  re-boot.

---

### Post by dryder on 2008-03-04
> has anyone tried with new captdrv160.tar.gz ?suoko, where are these new drivers please? All I can see are the (previous?) 150 drivers ...
Thanks,
David

---

### Post by dryder on 2008-03-04
Follow up ...

I found the  CAPTDRV[COLOR="Red"]160[/COLOR].tar.gz 10311.21 Kb driver on the Europe site:
Version  1.60        Released on   [COLOR="Red"]**21-01-2007**[/COLOR].

and two Linux Printer Drivers (CAPT) and Linux Printer Driver(CAPT) Ver.[COLOR="Red"]1.50E[/COLOR] (both these required from the Oz site) 
Ver.[COLOR="Red"]1.50E[/COLOR] Last Updated : [COLOR="Red"]**26-Feb-2008**[/COLOR].

Which is the most recent??

David

---

### Post by pmorton on 2008-03-15
The CAPTDRV160.tar.gz is the latest. And having just done a re-install on Ubuntu 7.10 of my LBP5000 using the 1.6 driver, and following the instructions in Canon's guide  (once untarred, view the manual by opening  the file manual_contents.html in your browser), it worked first time. No complaints this time!

---

### Post by dryder on 2008-03-16
Thanks pmorton,

David

---

### Post by dryder on 2008-04-11
Hi,
**SOLVED**
HARDY 64AMD

I have installed the 32-bit libraries ia32-libs, lib32asound2, lib32gcc1 and lib32stdc++6 but when trying to install the i386 debs as above I still get 'wrong architecture' errors.

What can I do to get these debs installed?

Many thanks,

David

---

### Post by dryder on 2008-04-12
Solved this without even doing a reboot -- from the guides by Jellus and pmorton I installed the i386 debians with the terminal instead of only trying th debian installer which has no force architecture setting.

LBP3000 works great in AMD64 Ubuntu ...

David

---

