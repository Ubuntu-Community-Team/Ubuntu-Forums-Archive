---
title: "Z11 printing"
date: 2006-07-22
forum: Desktop Environments
---

### Post by amunimanghi on 2006-07-22
Hi,

I have a Lexmark z11 printer and I'm trying to get it to work. First, I downloaded the .ppd and put it in /usr/share/cups/models. Next I configured my printer in the "Printers" application under System=>Administration. I selected the correct printer and used the driver that is in Ubuntu (see screenshot). After I downloaded the lz11-V2-1.2.tar.gz from sourceforge. I extracted it and ran the command ```
 sudo ./lz11.install
``` I followed the instructions and wanted to print a test page: ```
ameen@manghi:~/Desktop/lz11-V2-1.2$ sudo ./lz11.install

The following program will set up the
Lexmark Z11 / Compaq IJ300 printer driver.

Pick one of the following available options:

***************************************************
To do a new installation, you must first uninstall!
***************************************************
4) Print test page
5) Uninstall (needed before a new installation can be done)
7) Print Skew Adjustment test page for the Black Cartridge
8) Show README file ( <q> to return )
0) Quit

-> 4


Select the printer (or the interface), which refers to the Lexmark Z11
via which you want to print

Be sure that you do not try to print on a non-Z11 printer device

1) Z11
0) Quit

-> 1

printing: request id is Z11-9 (1 file(s))

```
It recognizes my printer so thats good. It just hangs at the printing page(see screenshot). My printer is turned on. It's connected through LPT #1. Thanks in advanced.

---

