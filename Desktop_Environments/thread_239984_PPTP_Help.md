---
title: "PPTP Help"
date: 2006-08-20
forum: Desktop Environments
---

### Post by g77s80 on 2006-08-20
Hi all,

I've installed an HP machine with KUbuntu 6.06 and have been trying to connect to the internet via an Alcatel speed touch home that uses PPTP.
I've installed pptpconfig and all extra software and have configured my network settings thus:
IP 10.200.1.1
Subnetmask 255.0.0.0

Target server 10.0.0.138

I keep getting the following messages:

1. MPPE required but MS CHAP[V2] auth not performed
2. PAP authentication failed

I've tried changing encryption settings in gui of pptpconfig but the result is always the same

I've also testing the network connection with a pppoe based modem and it works just fine 

ThanX

---

### Post by 1oki on 2006-08-21
check this thread out... it may or may not help, but we are currently discussing pptp and pptpconfig... 


[http://www.ubuntuforums.org/showthread.php?t=236710](http://www.ubuntuforums.org/showthread.php?t=236710)

Im sure their should be someone there on that thread that you could PM for help.

good luck

L

---

### Post by marianom on 2006-08-25
Hi, take a look @
[http://pptpclient.sourceforge.net/howto-diagnosis.phtml#mppe_bmanp](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#mppe_bmanp)
There's an entry for "MPPE required, but MS-CHAP[v2] auth not performed" and a suggested solution.

---

