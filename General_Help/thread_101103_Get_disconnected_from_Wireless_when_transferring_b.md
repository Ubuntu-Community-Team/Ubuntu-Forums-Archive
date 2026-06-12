---
title: "Get disconnected from Wireless when transferring big files"
date: 2005-12-09
forum: General Help
---

### Post by elvisd on 2005-12-09
Hi all,

I have a very strange issue: I connect to a Wireless Network, everything work fine, but when I should download a big file over the local Network the connection restarts :confused: . I have tried using wget, ftp and samba transfers. Anytime after 70-100 Mb of transfer the connection restarts...

I use Wireless Connection Manager 1.09 as connection manager, I have an IBM R51 Thinkpad (Integrated wireless), if more infos are needed ask... I'm a newbie... but i'll try ;) 

Is this caused by my Laptop? by the Access Point? By the Network Manager Applet? Or anything else?

Any help or suggestion is appreciated


Best regards


elvisd

---

### Post by lysis on 2005-12-09
ever have this problem with the same equipment using windows?

have you tried downloading things from the internet of a large size?  

if so, do you have the same problem when downloading from the net, or is it ONLY when it's from the local network.

we need to isolate the problem more. i know you mentioned that you've used several programs and it's just not happening.

---

### Post by elvisd on 2005-12-10
hi,

this problem with windows and same equipement doesn't exist.
When I download big files from the internet i have no problem.

The problem only appears when downloading at high transfer rates.
Even tried to limit the upload rate in my ftp server and transfer works. Downloading at high transfer rates hangs up...

Strange...:confused: 

elvisd

[FONT="Courier New"]elvisd@TPED:~$ uname -r
2.6.12-10-686
[/FONT]

---

### Post by elvisd on 2005-12-20
Hi all,

This problem persists... someone has some advice?

---

### Post by BathroomNinja on 2005-12-20
What router are you using and what wireless protocol (ie, B, G)? What is the program you are using on BOTH ends to share the file and to download the file? Are both boxes Ubuntu or is one windows or some other version of linux?

---

### Post by elvisd on 2005-12-21
Ok. Here the more detailed possible configuration description.

PC1 (Laptop):
 - IBM Thinkpad R51 1829-9MG
 - OS is Ubuntu Breezy (kernel 2.6.12-10-686)
 - Connection type: Wireless
 - Wireless Protocol: Don't know where should I check... ;-)
 - Network manager: gtkwifi before and Netswitch now (same problem...)

PC2
 - IBM Netvista
 - OS is Windows XP Professional
 - Connection Type: Ethernet (cable)

AP
 - DLink DWL-2100AP ([http://www.dlink.de](http://www.dlink.de))
 - Wireless Access Point with integrated Ethernet Switch

Transfer:
I've tried both Windows Share and ftp transfer (using gFtp and Firefox) and the problem exists in both cases.

---

### Post by funkymonkey on 2005-12-21
Check to see what your wireless adapter is.  I think some IBM laptops come with the Intel Centrino chipset, and so you might have the Intel 2200 wireless adapter, which a lot of people have trouble with (myself included).

---

### Post by elvisd on 2005-12-22
thank you, funkymonkey.

Here's my exact TP configuration:

 - P M 735
 - 512MB RAM
 - 60GB HDD
 - 15 SXGA+(1400x1050) TFT LCD
 - 32MB ATI Radeon 9000
 - CD-RW/DVD-R Multi-Burner
 - **Intel 802.11b/g wireless(MPCI)**
 - Bluetooth/Modem(CDC)
 - 1Gb Ethernet(LOM)
 - Secure Chip
 - IEEE 1394
 - 6 cell Li-Ion battery
 - WinXP Pro **(No-no-no! Ubuntu now!)**

Is this the wireless network card that causes problems?

**EDIT**
Link to my Thinkpad model:
[http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=1829-9mg](http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=1829-9mg)

---

