---
title: "KDE (?) printing problems"
date: 2006-01-26
forum: Desktop Environments
---

### Post by olale on 2006-01-26
Hi!

I've had several, possibly related, problems concerning my printer. The printer is a Samsung ML-1750 which I ironically chose for its documented official Linux support. Now I have experienced problems printing that prevent me from printing more than the first of a series of pages from a PDF. After the first page is printed, the printer refuses to respond and I must reboot and reinstall the printer in CUPS in order to make it work.

Some additional information on my system and previous experiences with printing under Kubuntu:

---

I am using Kubuntu Breezy with KDE 3.5 and have not used the printer extensively so I cannot say for sure when this happened, or even if it has been like this ever since I installed Kubuntu.

A few days ago I couldn't communicate with the printer at all and discovered that I had to make udev relax the permissions of /dev/usb/lp* to 0666 from 0660 in order for CUPS to talk to it, although cupsys belonged to the lp group and /dev/usb/lp0 also did, when the permissions were 0660.  

Also, in the system services menu cups shows up as a service that is listed as "not running", though I am pretty sure it is (I can talk to it through gnome-cups-manager at least, as well as see the running process).

The KDE printer manager also fails to restart the cups server with the message "couldn't communicate with the CUPS server" or something like that. However, modifying the printer properties from the KDE print manager seems to work.. 

---

Sometimes I can print test pages directly after I have successfully installed the printer, but the printer freezes after only one page of a multi-page printout has been processed. /var/log/cups/error_log gives no information about errors now however, it only tells me some filters have been initialized and the job is queued..

---

### Post by olale on 2006-01-30
Solution:

I reinstalled the printer with a different driver that default, as suggested by a user at linuxprinting.org. The driver for Samsung ML 4500 seemed to work much better..

---

### Post by Studymore on 2006-03-24
I started a thread with no reply, but I thought I would also respond here to maybe get a reply.  I can not get a printer to work on my system.

Here are the error messages:

In the KDE Control Center (running as root.)
Peripherals -> Printers ->
Unable to retrieve the printer list. Error message received from manager:
Connection to CUPS server failed. Check that the CUPS server is correctly installed and running. Error:
connection refused.

> From there, we can hopelessly attempt to add a printer.  This will be unsuccessful, of course,

because it can not connect, but I want to show you the error message:

Add -> Add Printer/Class ->

An error occurred while retrieving the list of available backends:

Connection to CUPS server failed. Check that the CUPS server is correctly installed and running.

Then, we can go into the Add Printer Wizard, which (since a retrieval of the available backends was
unsuccessful) will be unfruitful.  Backend selection is empty because backends were not retrieved.

When we try to open localhost:631 in Konqueror, we receive this message:

An error occurred while loading [http://localhost:631/:](http://localhost:631/:)
Could not connect to host localhost (port 631).

Pinging localhost shows the same problem,
localhost:631 does not respond.

Both commands:
sudo /etc/init.d/cupsys restart    &
sudo /etc/rc2.d/S19cupsys restart
yield this response:
* Restarting Common Unix Printing System: cupsd                      [ ok ]

But,. when we run this command:
ps -Al | grep cupsd
We get no reply.

Cups is obviously not running, but Linux is lying to
me....  arrggghhhhh!!!!

---

### Post by esteve on 2006-04-16
Same here, no solution yet.

---

