---
title: "Cannot get Scanners to work in Maverick with Xsane"
date: 2010-10-04
forum: Desktop Environments
---

### Post by andreseso on 2010-10-04
Hello,

With Lucid I was capable of scanning both with my Epson Perfection 640 U scanner and with my HP-M1120n-MFP network scanner.  To get the HP-M1120n to work I had to rename a file which I do not remenber which was.  I do not remember where I found the instructions.

I am running HPLIP 3.10.6 with Device Manager 15.0

I did a fresh install of Maverick Beta and I am not able to neither scan with the Epson Perfection scanner nor with the M1120n-MFP.  As said, both worked with Lucid.  As said I had to rename a file to get the MFP scanner to work.

I include screen shots to this post

---

### Post by 73ckn797 on 2010-10-09
I have been having issues with 10.04 and my HP J4580 All-in-One scanner function. The problems began just after installing 10.04. I believe that it is because Ubuntu quit including Xsane in the distribution as the default scan program. They now use Simple-scan. As the 10.04 updates have progressed the scanner issues have only become worse. 

I removed xsane and started using simple-scan which does not give me the problems. Simple-scan, however, does not do automatic file saving or incremental file numbering. It wants to save each scan as the same name which will overwrite the previous scan. I have to manually save each scanned page.

I am looking into other programs available to see if I can get back the ability to scan multiple documents and have the automatic, incremental file saving feature again.

---

### Post by andreseso on 2010-10-11
Execute gksudo gedit /etc/sane.d/dll.conf
Comment epson2, uncomment epson
Execute sane-find-scanner
Gives 
found USB scanner (vendor=0x04b8 [EPSON], product=0x010c [Perfection640  ]) at libusb:003:002
Edit /etc/sane.d/epson.conf
Add line
# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
usb 0x04b8 0x010c

Reboot

Xsane now is able to scan from this scanner.

Reference
[https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/478761](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/478761)

---

### Post by The Cog on 2010-10-11
Woo Hoo! Thank you, Andreseso.

I haven't tried xsane, but I find that your first change made simple-scan work with my Epson Perfection640:
edit /etc/sane.d/dll.conf and find the lines:
> #epson
epson2and change them to look like this instead:
> epson
#epson2

P.S. 
It seems there is no need to reboot - just restart simple-scan. 
Maybe xsane needs saned, but simple-scan appears not to.

---

### Post by brimurray on 2010-10-11
> **The Cog said:**
> Woo Hoo! Thank you, Andreseso.

I haven't tried xsane, but I find that your first change made simple-scan work with my Epson Perfection640:
edit /etc/sane.d/dll.conf and find the lines:
and change them to look like this instead:

P.S. 
It seems there is no need to reboot - just restart simple-scan. 
Maybe xsane needs saned, but simple-scan appears not to.
Brilliant, this simple trick worked for me too, I can now use Simple Scan and Xsane with my Epson CX3200. Thank you.

---

### Post by trukker on 2010-10-25
xsane works with this fix for me, but simple scan doesnt :(

---

### Post by cholt45 on 2010-11-30
Hello!
Thanks for sharing this info, it solved my problem with epson cx3200 on ubuntu 10.10 . It worked for me without rebooting and both xsane and simle scan are working like a charm. 
Thanks,
cholt45

---

### Post by chessert on 2011-05-03
Thank you very much!  The first change (epson2 --> epson) worked for my Epson CX3200 connected to Maverick 10.10 64-bit.  :p

---

### Post by andreseso on 2011-05-06
Same instructions work in Natty. I must have overwritten all my config files during the upgrade because my scanner did not work.

Love

---

