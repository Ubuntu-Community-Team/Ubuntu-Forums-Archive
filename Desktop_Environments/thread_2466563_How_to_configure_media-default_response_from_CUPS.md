---
title: "How to configure media-default response from CUPS"
date: 2021-08-30
forum: Desktop Environments
---

### Post by ski-brimson on 2021-08-30
I have investigated KDE Kate, and it uses http to request from cups the printer settings.  One of the responses from CUPS is media-default, and it is currently set to iso_a4_210x297mm in the URL response.  This is not correct for my printer.

I have already tried setting the media size in lpoptions, but it does not fix this CUPS web response that is used by KDE Kate.

For instance, lpoptions -l has this response:
[INDENT]PageSize/Media Size: A3 A4 A5 A6 B4 B5 ISOB5 B6 OficioII Folio Statement P8K P16K OficioMX *Letter Legal Executive Tabloid EnvPersonal Env9 Env10 EnvMonarch EnvDL EnvC5 EnvC4 Custom.WIDTHxHEIGHT
[/INDENT]

Even though it is set to Letter, this does not affect the Web interface to CUPS that KDE uses.

If I try to set media-default using lpoptions, it doesn't seem to take:

[INDENT]lpoptions -d Kyocera_TASKalfa_3212i -o "media-default=Letter"
[/INDENT]



How can I change "iso_a4_210x297mm" to the appropriate value for "Letter", whatever that might be?

---

### Post by him610 on 2021-08-30
What make and model of printer? Kyocera ???
How is printer connected to your computer? USB, Cat 5, or wireless?
Which version of *buntu are you running?
```
 uname -a
```
Have you tried setting default 'Letter' page in printer setup?
I do not have a Kyocera printer, but I do have two other printers where I can access the each printer's setup page by entering the IP address of the printer. I would think you should be able to do the same. 
This is the paper size setting for one of my printers....
[IMG]https://imgur.com/PdBQO4Q.png[/IMG]
The other printer uses a menu driven LCD panel to select page size.

---

### Post by ski-brimson on 2021-09-02
This is a large corporate printer.  Needless to say it works fine with windows.  The printer configuration is out of my control.

The default paper size is set to A4 in the ppd file.  Is there a way to over-ride it?[INDENT]*DefaultPageSize: A4
[/INDENT]
[INDENT]
[/INDENT]
I do not have this issue in GTK applications.

KDE applications query CUPS as I mentioned, and the information given by CUPS is not correct for the printer.

KDE is opening this socket:

/var/run/cups/cups.sock

cups.sock is created by cupsd.

ii  cups-daemon                         2.1.3-4ubuntu0.11      amd64                  Common UNIX Printing System(tm) - daemon

I downloaded the PPD file from Kyocera's web site and installed it using the CUPS Web-UI.

Ubuntu is 16.04.7.

---

### Post by him610 on 2021-09-02
> Ubuntu is 16.04.7
You [COLOR="#FF0000"]really need to update[/COLOR] to a current version of Ubuntu.

I am using Xubuntu, but I assume the CUPS interface is the same for both.
Try this....
Open Settings, highlight your Kyocera printer,
Right click your mouse, on the dropdown list, select Properties,
On the left side listing, click on Printer Options,
Media Size is where you select the paper size.

---

