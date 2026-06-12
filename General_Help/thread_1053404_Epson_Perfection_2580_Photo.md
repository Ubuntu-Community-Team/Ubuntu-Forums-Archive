---
title: "Epson Perfection 2580 Photo"
date: 2009-01-28
forum: General Help
---

### Post by OffHand on 2009-01-28
Hi all,

I got the Epson Perfection 2580 Photo scanner. Works alright with Xsane but since that is butt ugly I wanted to use gnomescan. The GUI of gnomescan is called flegita. That application crashes when probing devices:

The scan backend returned the following error: Invalid argument


From the command line: 

$ flegita
(flegita:11228): GnomeScan-DEBUG: gnomescan 0.4.1
(flegita:11228): GnomeScan-DEBUG: sane_init(0xbfd7d298, NULL)
(flegita:11228): GnomeScan-DEBUG: SANE Version = 1.0.19
(flegita:11228): GnomeScan-DEBUG: sane_get_devices (0xbfd7d288, FALSE)
(flegita:11228): GnomeScan-DEBUG: Invalid argument

Help appreciated!

---

### Post by OffHand on 2009-01-29
bump

---

### Post by mjaga on 2009-04-08
I am having exactly the same problem with an HP C3180 printer/scanner, works fine with
Xsane but with flegita I get:
(flegita:21619): GnomeScan-DEBUG: gnomescan 0.4.1
(flegita:21619): GnomeScan-DEBUG: sane_init(0xbfa88f48, NULL)
(flegita:21619): GnomeScan-DEBUG: SANE Version = 1.0.19
(flegita:21619): GnomeScan-DEBUG: sane_get_devices (0xbfa88f38, FALSE)
(flegita:21619): GnomeScan-DEBUG: Invalid argument

Have you been able to solve your problem in the meantime?

---

### Post by alberhg on 2009-08-11
I fixed my problem with an EPSON DX6000 and an internal webcam by updating to version 0.6.1 from the author's PPA...

[http://ppa.launchpad.net/bersace/ppa/ubuntu](http://ppa.launchpad.net/bersace/ppa/ubuntu)

---

### Post by OffHand on 2009-08-13
> **alberhg said:**
> i fixed my problem with an epson dx6000 and an internal webcam by updating to version 0.6.1 from the author's ppa...

[http://ppa.launchpad.net/bersace/ppa/ubuntu](http://ppa.launchpad.net/bersace/ppa/ubuntu)

ty!

---

