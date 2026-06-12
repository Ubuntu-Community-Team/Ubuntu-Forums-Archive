---
title: "printing not working in xfce"
date: 2008-03-30
forum: Desktop Environments
---

### Post by keratos on 2008-03-30
Tried these but no joy.

[http://www.cups.org/cups-help.html](http://www.cups.org/cups-help.html)
[http://www.linuxprinting.org/~till/printing-tutorial/tut.html](http://www.linuxprinting.org/~till/printing-tutorial/tut.html)

I'm having a NIGHTMARE trying to get my Epson Stylus R800 printing under XFCE4.

I have installed the following packages:
```

cupsys
cupsys-client
cupsys-common
foomatic-db-engine
foomatic-db
foomatic-filters

```

I then turned to localhost:631 in my browser and added a printer. My USB Epson was listed so I selected it. The CUPS interface appears to show my printer installed and available.
```
# lpstat -t
scheduler is running
system default destination: EpsonR800
device for EpsonR800: usb://EPSON/Stylus%20Photo%20R800
EpsonR800 accepting requests since Sun 30 Mar 2008 22:26:12 BST
printer EpsonR800 is idle.  enabled since Sun 30 Mar 2008 22:26:12 BST

# ls | lp
request id is EpsonR800-18 (1 file(s))

```

Nothing prints out. I tried a test page print from the CUPS web interface, nothing happens. 

I'm stuck now and very confused with Ghostscript, CUPS, foomatic, Gutenprint, LPr, lp and so on arrg...

Of course GNOME does this simply - It just "worked" however xfce is proving more challenging.

Can someone please guide me. 

I've attached a tar file that includes some essential CUPS config and output from /var/log/cups/

I'm not sure my PPD is correct but would have no idea anyway, on how to "fix it"?

Can someone please assist, thanks

---

### Post by warp99 on 2008-03-31
Do you have the print manager installed? 

[http://packages.ubuntu.com/gutsy/xfprint4](http://packages.ubuntu.com/gutsy/xfprint4)

Last time I loaded Xubuntu the printer would not work until I loaded the print manager.

---

### Post by keratos on 2008-03-31
yes I did.

it correctly identifies the printer as available and allows me to set it as default.

However, as stated above, nothing comes out of the printer.

From what I have read, I should be able to print a test page from the CUPS web interface (localhost:631) but again, nothing comes out. I am therefore minded to assume this is a linux/cups issue and not xfce, because I cannot print from the CUPS web interface (i.e. the server end of the printing system). XFCE et.al would be clients to the serverm if I understand things correctly.

---

