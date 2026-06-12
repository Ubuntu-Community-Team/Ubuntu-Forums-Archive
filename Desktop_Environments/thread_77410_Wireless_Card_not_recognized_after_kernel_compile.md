---
title: "Wireless Card not recognized after kernel compile"
date: 2005-10-16
forum: Desktop Environments
---

### Post by mog27 on 2005-10-16
I have a Netgear WAG511 Cardbus card.  It is recognized fine during the Breezy install.  I went ahead and compiled a vanilla kernel (off kernel.org) and did a make oldconfig.  Booting into that kernel (2.6.13.4), my Netgear card is not recognized.  

I thought I needed to reinstall ndiswrapper.  However, this does **not** use ndiswrapper.  I confirmed that by going into my install kernel (with the card recognized and working) and checking to see if ndiswrapper was being used and installed.  It was not being used nor installed.  So my question is, what the heck was it using during the default breezy kernel?  I thought make oldconfig would have brough ALL modules and such over.  Any suggestions?

---

### Post by mog27 on 2005-10-16
I got it working fine now.  I installed the madwifi drivers under the new kernel.

---

