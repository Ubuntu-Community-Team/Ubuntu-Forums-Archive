---
title: "Please help with HP Deskjet printer setup!"
date: 2008-12-30
forum: General Help
---

### Post by hyperyoda on 2008-12-30
Hi everyone,

This is very frustrating because everything seems correct, yet it still doens't work.

Here is what I've done to get my HP Deskjet 960c color inkjet printer working in Ubuntu 6.06 (Dapper Drake):

Booted up, hooked my printer up to the parallel port and powered it on, added paper, printer's green light is on.

I then went to System -> Administration -> Printing
Clicked on New Printer and it ran gnome-cups-add and read the printer database

Then the Add a Printer dialog box says:
Step 1 of 3: Printer Connection
Printer Type: local printer
Use a detected printer: HP DESKJET_960C

It has in Printer Port: (greyed out so I can't change it):
hp:/par/DESKJET_960C?device=/dev/parport0 (HP DESKJET_960C)

So it detected my correct printer.

Then I went Forward to:
Step 2 of 3: Printer Driver
Manufacturer: HP
Model: Deskjet 960C
Driver: hpijs (recommended) - HPLIP 0.9.7 (Suggested) There is a green dot after this showing it is installed.

Then I went Forward to:
Step 3 of 3: Printer Information
Name: Deskjet
Description: HP-DESKJET
Location: home

So after I filled those in I clicked Apply.

But when I go back to the Printers control panel I don't see any printer in there. It just says has the New Printer icon to create a new printer. It should have created the printer I setup. And when I try to print it said in the console: lpr: Error - no default destination available. So apparently it is not setting it up :-( 

I checked the log files and only thing I saw possibly relevant was in /var/log/syslog:

Dec 31 01:18:29 ubuntu kernel: [4498844.439000] lp0: ECP mode
Dec 31 01:18:30 ubuntu kernel: [4498844.757000] lp0: ECP mode
Dec 31 01:18:33 ubuntu kernel: [4498847.541000] ppdev0: registered pardevice
Dec 31 01:18:33 ubuntu kernel: [4498847.570000] ppdev0: negotiated back to compatibility mode because user-space forgot
Dec 31 01:18:33 ubuntu kernel: [4498847.570000] ppdev0: unregistered pardevice
Dec 31 01:18:36 ubuntu kernel: [4498851.283000] lp0: ECP mode

I verified I have the correct drivers installed:

ubuntu@ubuntu:~$ dpkg -l|grep hplip
ii  hplip                                  0.9.7-4ubuntu1 HP Linux Printing and Imaging System (HPLIP)
ii  hplip-data                             0.9.7-4ubuntu1 HP Linux Printing and Imaging - data files
ii  hplip-ppds                             0.9.7-4ubuntu1 HP Linux Printing and Imaging - PPD files
ubuntu@ubuntu:~$ dpkg -l|grep hpijs
ii  foomatic-db-hpijs                      1.5-20060318-1 linuxprinting.org printer support - database
ii  hpijs                                  2.1.7+0.9.7-4ubuntu1 HP Linux Printing and Imaging - gs IJS drive

Is there a way I can manually force it to try and print using the drivers? It should work, I followed all the steps yet it never creates an entry for my printer :-( What is wrong?

Zach

---

### Post by 2hot6ft2 on 2008-12-30
Do you have System>Preferences>HPLIP Toolbox ? If not perhaps it would help you get it straightened out I'm sure it's in the repos since it came on mine and HP Printers is what it's for.

---

### Post by hyperyoda on 2008-12-30
> **2hot6ft2 said:**
> Do you have System>Preferences>HPLIP Toolbox ? If not perhaps it would help you get it straightened out I'm sure it's in the repos since it came on mine and HP Printers is what it's for.

Hi, no I don't have it. There is nothing in System->Preferences relating to printers. Do you know where I can download a .deb for this for Dapper Drake (Ubuntu 6.06). I run off a Live CD (no hard disk) so I hope the package is not too big so I can install it.

Zach

---

### Post by hansdown on 2008-12-30
Hi hyperyoda.
You need to install hplip toollbox by going to System> administration> synaptic package manager.

By the by, A google search of your particular question turned up some nasty surprises if you use microsoft os.

---

### Post by 2hot6ft2 on 2008-12-30
Like he said go to System>Administration>Synaptic Package Manager click on search put in hplip hit search when it shows up click on the box and Mark For Installation then hit Apply and it will install it.

Since you said you're running on a livecd if you want to save the package so you can use it again.

After you mark it click on File>Create Download Script. Tell it where to save the script. Then you can double click on the script and select run OR run in terminal and it will download the package into the same folder where the script is.

That way you can save it. You can always install it by double clicking on it.

---

### Post by hyperyoda on 2008-12-31
I have hplip installed. I found the program that adds the printer is gnome-cups-manager which calls gnome-cups-add so I ran that, but after I go through and select everything (ran 'sudo gnome-cups-manager') it still doesn't add the printer and in the console it says:
** (gnome-cups-add:28853): WARNING **: IPP request failed with status 1280

I found this is /var/log/cups/error_log:
E [31/Dec/2008:08:15:02 -0500] CUPS-Add-Modify-Printer: Unauthorized

I ran as root this time (sudo) so I don't understand why it is saying
I am unauthorized.

And I found this in /var/log/cups/access_log:
localhost - - [31/Dec/2008:08:14:18 -0500] "POST / HTTP/1.1" 200 1652
CUPS-Get-Devices -
localhost - - [31/Dec/2008:08:14:26 -0500] "POST / HTTP/1.1" 200
652837 CUPS-Get-PPDs -
localhost - - [31/Dec/2008:08:15:02 -0500] "POST /admin/ HTTP/1.1" 401
352 CUPS-Add-Modify-Printer successful-ok
localhost - root [31/Dec/2008:08:15:02 -0500] "POST /admin/ HTTP/1.1"
200 352 CUPS-Add-Modify-Printer server-error-internal-error

Zach

---

### Post by hyperyoda on 2008-12-31
> **hansdown said:**
> Hi hyperyoda.
You need to install hplip toollbox by going to System> administration> synaptic package manager.

By the by, A google search of your particular question turned up some nasty surprises if you use microsoft os.

I have hplip but I can't run hp-toolbox because I run Ubuntu Live CD (my hard disk controller died on my laptop) and hp-toolbox needs the package python-qt3 which needs 20MB of disk space to install and I just don't have that much space in my ramdisk. The most I have is like 5MB free :-(

Zach

---

### Post by hyperyoda on 2008-12-31
> **2hot6ft2 said:**
> Like he said go to System>Administration>Synaptic Package Manager click on search put in hplip hit search when it shows up click on the box and Mark For Installation then hit Apply and it will install it.

Since you said you're running on a livecd if you want to save the package so you can use it again.

After you mark it click on File>Create Download Script. Tell it where to save the script. Then you can double click on the script and select run OR run in terminal and it will download the package into the same folder where the script is.

That way you can save it. You can always install it by double clicking on it.

I already have hplip and hpijs installed.

Zach

---

### Post by hansdown on 2008-12-31
Hi hyperyoda.

Just for the heck of it, go to the top of the browser screen, and click file. The drop down menu should have print. Select it and see if it does anything.

---

### Post by hyperyoda on 2008-12-31
> **hansdown said:**
> Hi hyperyoda.

Just for the heck of it, go to the top of the browser screen, and click file. The drop down menu should have print. Select it and see if it does anything.

It doesn't print.

Zach

---

### Post by hyperyoda on 2008-12-31
I even tried the cups web interface: [http://localhost:631/admin](http://localhost:631/admin)

I selected Add Printer and choose my model HP960C and the hplip driver but when I go to apply it says: 
413 Request Entity Too Large

Ugh every single thing I've tried has failed and for no apparent reason. Any way I can try to get the printer working directly with lpr without using CUPS?

Zach

---

### Post by hyperyoda on 2009-01-01
I have exhausted every solution I could find :( As a last resort I tried running lpadmin to set the printer manually and I get that stupid ambiguous error message again, same one I got in the cups web interface. Does anyone know what this error message means and how  I can get my printer (HP Deskjet 960C hooked up to parallel port) setup using lpadmin:

ubuntu@ubuntu:~$ sudo lpadmin -h localhost -p HP -D printer -u allow:ubuntu -P /rofs/usr/share/cups/model/hpijs/HP/HP-DeskJet_960C-hpijs.ppd
lpadmin: Request Entity Too Large

Zach

---

### Post by hansdown on 2009-01-01
Hi hyperyoda.
My skills are very limited, but I found a ppd that may be helpful.

[http://openprinting.org/show_driver.cgi?driver=hpijs](http://openprinting.org/show_driver.cgi?driver=hpijs)

---

### Post by hyperyoda on 2009-01-02
> **hansdown said:**
> Hi hyperyoda.
My skills are very limited, but I found a ppd that may be helpful.

[http://openprinting.org/show_driver.cgi?driver=hpijs](http://openprinting.org/show_driver.cgi?driver=hpijs)

Hi, I already tried that one heh.

Zach

---

