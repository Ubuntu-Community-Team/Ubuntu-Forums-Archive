---
title: "Replacing wireless card inspiron 1501"
date: 2007-10-31
forum: Dell  Ubuntu Support
---

### Post by coolclassic on 2007-10-31
I plan to replace the wireless card in my laptop. what i need to know if this is possible. I understand that a pcimini card would fit can this be confirmed. What is the best card to replace it with? I have seen a card on ebay with the Atheros Chipset see link: [http://cgi.ebay.co.uk/802-11G-MINI-PCI-CARD-WIFI-LAPTOP-WIRELESS-LAN-NETWORK_W0QQitemZ130167739763QQihZ003QQcategoryZ74954QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.co.uk/802-11G-MINI-PCI-CARD-WIFI-LAPTOP-WIRELESS-LAN-NETWORK_W0QQitemZ130167739763QQihZ003QQcategoryZ74954QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)
Is this card any good?

---

### Post by jpittack on 2007-10-31
Why would you want to replace one wireless card with another that will accomplis the same thing?  Both support G speeds and the current card supports up to WPA2.

---

### Post by coolclassic on 2007-10-31
Propper driver support

---

### Post by jpittack on 2007-10-31
Have you tried using the ndiswrapper solution?  I have had no problems with this.

---

### Post by theurgy on 2007-10-31
I replaced my Broadcom 4311 with an Atheros Super G card.
I tried the Intel 3945ABG and it wouldn't work, my 1501 wouldn't even post. I suspect it needed an Intel CPU for the whole Centrino package to work.

---

### Post by tturrisi on 2007-11-01
I replaced the broadcom wifi on my dell d830 w/ an atheros card.
Mine is a mini-pciE card.  Verify that yours is mini-pci or mini-pci express.  Most newer laptops from dell are mini-pci express cards.
AFAIK the 1501 uses a mini-pci express card.
Get them here:
[http://www.oxfordtec.com/us/](http://www.oxfordtec.com/us/)
Mine arrived in 3-4 days after placing the order.
DON'T get atheros cards with AR5006, AR5007, or AR5008
Get this one:
[http://www.oxfordtec.com/us/MiniPCI-EXPRESS-Wireless-Cards/c42/p113/GIGABYTE-WI01GT-miniPCI-EXPRESS-Wireless-card---Atheros-Super-G-108-Mpbs-AR5005GS-mini-PCI-E,-mPCIe-adapter/product_info.html](http://www.oxfordtec.com/us/MiniPCI-EXPRESS-Wireless-Cards/c42/p113/GIGABYTE-WI01GT-miniPCI-EXPRESS-Wireless-card---Atheros-Super-G-108-Mpbs-AR5005GS-mini-PCI-E,-mPCIe-adapter/product_info.html)

---

### Post by bluedragon436 on 2007-11-03
I have swapped mine out with the same one that Tturrisi is mentioning there in his post, and Ubuntu worked just fine wiht it, and I have no problems connecting to WPA2 either...not bad pricing either for what you get out of it...

---

### Post by mblind on 2007-12-05
ok, after you swap out the card and restart Ubuntu what do you need to do for the system to see the card?

---

### Post by tturrisi on 2007-12-11
> **mblind said:**
> ok, after you swap out the card and restart Ubuntu what do you need to do for the system to see the card?

The system will immediately see the card, but you will need to install the madwifi drivers:

```
apt-get install build-essential subversion linux-headers-`uname -r`
cd /usr/src
svn  checkout http://svn.madwifi.org/madwifi/trunk/ madwifi-ng
cd madwifi-ng
make
make install
depmod -ae
modprobe ath_pci
```

---

