---
title: "Trying to install printer"
date: 2008-11-25
forum: Desktop Environments
---

### Post by Taadaa on 2008-11-25
I'm trying to install a Brother MFC-5460CN printer.  It's on my network and when I try to print to it, the LCD screen on the printer lights up saying it's receiving data but nothing happens.

Went to the Brother site and downloaded their deb package for this printer and went through the installation of the package.  Then when it came time to choose the printer driver from the list, it wasn't there.  Back to the Brother site and followed their linux installation instructions.  This is what I did and what I got:

carolyn@carolyn-Linux:~$ sudo aa-complain cupsd
sudo: unable to resolve host carolyn-Linux
[sudo] password for carolyn: 
Setting /etc/apparmor.d/usr.sbin.cupsd to complain mode.
carolyn@carolyn-Linux:~$ sudo mkdir /usr/share/cups/model
sudo: unable to resolve host carolyn-Linux
mkdir: cannot create directory `/usr/share/cups/model': File exists
carolyn@carolyn-Linux:~$ in -s /etc/init.d/cupsys /etc/init.d/lpd
bash: syntax error near unexpected token `in'
carolyn@carolyn-Linux:~$ In -s /etc/init.d/cupsys /etc/init.d/lpd
bash: In: command not found
carolyn@carolyn-Linux:~$ cd /var/spool/lpd
bash: cd: /var/spool/lpd: No such file or directory
carolyn@carolyn-Linux:~$ cd var
bash: cd: var: No such file or directory
carolyn@carolyn-Linux:~$ cd /
carolyn@carolyn-Linux:/$ cd /var
carolyn@carolyn-Linux:/var$ cd spool
carolyn@carolyn-Linux:/var/spool$ cd lpd
bash: cd: lpd: No such file or directory
carolyn@carolyn-Linux:/var/spool$ mkdir lpd
mkdir: cannot create directory `lpd': Permission denied

To my knowledge, I am logged in as administrator but it apparently won't let me create directly lpd which it seems, I need.  Any ideas??

C

---

### Post by Taadaa on 2008-11-27
Anybody have any ideas on this?  Please?

---

