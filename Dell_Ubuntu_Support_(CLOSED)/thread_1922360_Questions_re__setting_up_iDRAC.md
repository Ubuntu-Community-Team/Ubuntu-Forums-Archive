---
title: "Questions re:  setting up iDRAC"
date: 2012-02-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by djtopper on 2012-02-08
So I've set up a new R710 server with Ubuntu 10.04 LTS.  The machine has the latest, greatest iDRAC stuff from dell (eg., the iDRAC enterprise w/ SDCARD).  At the very least, this was the highest end option to purchase.

The thing is, I'm not clear at all about how to set it up.  I know that iDRAC is a type of virtual console, but I'm at a loss to find documentation about a) how to access it or as I said b) set it up on the machine.

Any pointers to info would be appreciated.

Thank,

DT

---

### Post by wgarider on 2012-02-08
> **djtopper said:**
> So I've set up a new R710 server with Ubuntu 10.04 LTS.  The machine has the latest, greatest iDRAC stuff from dell (eg., the iDRAC enterprise w/ SDCARD).  At the very least, this was the highest end option to purchase.

The thing is, I'm not clear at all about how to set it up.  I know that iDRAC is a type of virtual console, but I'm at a loss to find documentation about a) how to access it or as I said b) set it up on the machine.

Any pointers to info would be appreciated.

Thank,

DT
If you bought the Enterprise version, it would need a separate network cable. You configure it at the very end of the BIOS boot sequence - I forget the key combination but it occurs right after the RAID check is complete. It's relativity simple - needs only a few parameters and then all you do to access it over the LAN is to type the IP/DNS name you sued into your browser and you can manage the server remotely.....

See if this is useful to you: [http://support.dell.com/support/edocs/software/smdrac3/idrac/idrac10mono/en/ug/html/index.htm](http://support.dell.com/support/edocs/software/smdrac3/idrac/idrac10mono/en/ug/html/index.htm)

---

