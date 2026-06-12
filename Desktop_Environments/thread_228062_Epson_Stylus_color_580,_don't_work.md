---
title: "Epson Stylus color 580, don't work"
date: 2006-08-02
forum: Desktop Environments
---

### Post by luquino on 2006-08-02
Hi all! First of all I apologize for my poor english, I'm italian.
I jumped into linux world 4 weeks ago installing on my desktop pc ubuntu breezy from a cd and then I upgraded to dapper.
I had some problems in setting up my system, but now everything is fine except the printer.
I have an Epson Stylus Colors 580 wich driver is installed with the system (gutenprint), but I wasn't able to put this printer at work with dapper, it was ok with breezy

Here the details:
Cups version is 1.2.1
Pc is a desktop with AMD athlon 64 (so dapper is amd64 version)
the printer is connected in local via USB port.
I installed the printer with gnome printer manager
The printer is detected by the printer manager and it sets automatically the right driver
The printer in setted on USB #1 (in breezy the printer was setted on USB #0, but in dapper I can't get usb #0, neither in printer manager and in localhost:631)

When I try to print a test page with gnome printer manager it says:

ERROR 1034 - THE PRINTER IS PAUSED? (I hope this is the right translation)
But the printer is READY not PAUSED.


In the localhost facility everything seems to be fine, the printer is detected and configured, the printer icon shows the green led on, but if I try to print a test page it says:

Unsupported format 'application/postscript'!


If I try to print from command line this is the result:

luca@luca:~$ lp file.txt
lp: Unsupported format 'text/plain'!


This is the access_log file after a try (test page) from gnome printer manager:

localhost - - [15/Jul/2006:19:04:49 +0200] "POST / HTTP/1.1" 200 136 Get-Jobs successful-ok
localhost - - [15/Jul/2006:19:04:52 +0200] "POST / HTTP/1.1" 200 136 Get-Jobs successful-ok
localhost - - [15/Jul/2006:19:04:52 +0200] "GET /ppd/Stylus-Color-580.ppd HTTP/1.1" 200 65917 - -
localhost - - [15/Jul/2006:19:04:52 +0200] "POST /printers/Stylus-Color-580 HTTP/1.1" 200 155403 Print-Job client-error-document-format-not-supported
localhost - - [15/Jul/2006:19:04:55 +0200] "POST / HTTP/1.1" 200 136 Get-Jobs successful-ok


And this is error_log:

E [15/Jul/2006:18:07:46 +0200] Creating missing directory "/var/run/cups/certs"



This is the printers.conf file:

# Printer configuration file for CUPS v1.2.1
# Written by cupsd on 2006-07-17 23:53
<Printer epson580>
Info
Location
DeviceURI usb://EPSON/Stylus%20COLOR%20580
State Idle
StateTime 1153173224
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>


This is the header in epson.ppd:

*FormatVersion: "4.3"
*FileVersion: "5.0.0-rc2"
*LanguageVersion: English
*LanguageEncoding: ISOLatin1
*PCFileName: "STP00072.PPD"
*Manufacturer: "Epson"
*Product: "(AFPL Ghostscript)"
*Product: "(GNU Ghostscript)"
*Product: "(ESP Ghostscript)"
*Product: "(GPL Ghostscript)"
*ModelName:     "EPSON Stylus Color 580"
*ShortNickName: "EPSON Stylus Color 580"
*NickName:      "EPSON Stylus Color 580 - CUPS+Gutenprint v5.0.0-rc2"
*PSVersion: "(3010.000) 550"
*PSVersion: "(3010.000) 651"
*PSVersion: "(3010.000) 652"
*PSVersion: "(3010.000) 653"
*PSVersion: "(3010.000) 704"
*PSVersion: "(3010.000) 705"
*PSVersion: "(3010.000) 707"
*PSVersion: "(3010.000) 800"
*PSVersion: "(3010.000) 815"
*PSVersion: "(3010.000) 850"
*PSVersion: "(3010.000) 81501"
*LanguageLevel: "3"
*ColorDevice: True
*DefaultColorSpace: RGB
*FileSystem: False
*LandscapeOrientation: Plus90
*TTRasterizer: Type42
*cupsVersion: 1.1
*cupsModelNumber: "0"
*cupsManualCopies: True
*cupsFilter: "application/vnd.cups-raster 100 rastertogutenprint.5.0"
*cupsFilter: "application/vnd.cups-command 33 commandtoepson"

*StpDriverName: "escp2-580"
*StpPPDLocation: "/usr/share/ppd/gutenprint/5.0/C/stp-escp2-580.5.0.ppd.gz"
*StpLocale: "C"
*VariablePaperSize: true


Dmesg command for printer:

luca@luca:~$ dmesg | grep printer
[   47.512681] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
luca@luca:~$


In the lp group there are:

cupsys
hal
luca (my user)


I hope that someone can help me because I wanto leave windows at all, but this is impossible until my printer is not working.

Thank you to everyone for reading this.

---

### Post by luquino on 2006-08-08
Got it!!!!!!!!!   My printer is working now!

It was enough to uncomment this line in mime.convs file:

# pstoraster is now part of ESP Ghostscript...
application/vnd.cups-postscript application/vnd.cups-raster     100     pstoraster

By default the line is commented, due to the comment above (I suppose), but something is wrong....
So if someone get in trouble after a cups upgrade, try this before getting fool. It tooks one month to me to find out this.

Bye

---

### Post by dov_s on 2006-10-15
> **luquino said:**
> Got it!!!!!!!!!   My printer is working now!

It was enough to uncomment this line in mime.convs file:

# pstoraster is now part of ESP Ghostscript...
application/vnd.cups-postscript application/vnd.cups-raster     100     pstoraster

By default the line is commented, due to the comment above (I suppose), but something is wrong....
So if someone get in trouble after a cups upgrade, try this before getting fool. It tooks one month to me to find out this.

Bye

:) Thanks it help me a lot !!:D

---

