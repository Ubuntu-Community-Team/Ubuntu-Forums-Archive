---
title: "Scanner Issues--HP Scanjet 8250"
date: 2009-03-23
forum: General Help
---

### Post by js@lloyd on 2009-03-23
Still not able to scan. Typically, the 1st attempt to scan with xsane restarts my computer, then post attempts shuts down xsane app.  This is the output from running xsane in a terminal
(xsane:6790): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6790): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6790): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6790): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6790): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6790): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6790): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6790): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

Also, someone suggested running hplip-3.9.2.run. I saved it to my desktop, but can't run it. Can't open file.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Any help is appreciated. 
JS

---

### Post by js@lloyd on 2009-03-23
Hoping that there is someone out there that can assist.

Thanks,  JS

---

### Post by Alfred_McGee on 2009-04-04
Here's how I whipped this problem:

I used Syanptic Package Manager, marked xsane for complete removal, then removed it. In terminal, I then typed:

sudo apt-get install xsane

This also solved another problem I had had since upgrading to Ibex: Xsane would only run as root, which was annoying. Reinstalling an application is not the most elegant way to kill a bug, but it's easy, and in this case it works.

---

### Post by js@lloyd on 2009-04-04
> **Alfred_McGee said:**
> Here's how I whipped this problem:

I used Syanptic Package Manager, marked xsane for complete removal, then removed it. In terminal, I then typed:

sudo apt-get install xsane

This also solved another problem I had had since upgrading to Ibex: Xsane would only run as root, which was annoying. Reinstalling an application is not the most elegant way to kill a bug, but it's easy, and in this case it works.

I gave it a shot, but got the same results.  Xsane crashed my computer on the 1st attempt to scan to a PDF.  Same thing that's been happening all along.

[www.sane-project.org](www.sane-project.org) lists avision (Build: 201)as the backend for this particular scanner.  Can anyone tell me how I might go about downloading/installing that?  

Thanks,  JS

---

### Post by geraldm on 2009-04-05
the avision backend is among those backends installed with the sane packages.
It is in the sane-backends package.  I have seen recent remarks that the avision backend does not have a current maintainer upstream, so it would be better to use a ubuntu or debian package.

regards,
Gerald

---

### Post by Camilia on 2009-04-07
I can't get my scanjet to work either. I have had it working previous before I did a restore

Pasted sudo apt-get install xsane and got

Reading package lists... Done
Building dependency tree       
Reading state information... Done
xsane is already the newest version.

It still won't work I have unplugged plugged the outlet into speakers and it worked. Plugged usb connector into different outlets.

Unplugged the outlet to scan jet a few time and finally working.

---

### Post by bo_n_tulsa on 2009-04-24
aarrgh!!  This is very frustrating.  I have the same error messages as the very first post here.  I actually got xsane to scan a greyscale image to my home folder, but right when it scanned it and dumped the file there it crashed.  Then the scan was very poor.

Can anybody help us with this?

thx

---

