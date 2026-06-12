---
title: "How to manage a wifi card swap?"
date: 2006-02-14
forum: Desktop Environments
---

### Post by Sendervictorius on 2006-02-14
Hi,

My wifi card has just died, and I have bought a D-Link DWL-G520 PCI card to replace it. According to my research, it should "just go", since it contains an Atheros chipseet.

My question is this: The old card was set up with ndiswrapper. Do I have to do anything to uninstall the module, or do I just swap the two PCI cards over and reboot. Will my connection parameters set up for my last card (WEP key etc) still work?

Cheers,
Andrew

---

### Post by Sendervictorius on 2006-02-15
Well, I can sort of answer my own question. I thought I would just swap the cards and see what happens. The parameters were wiped out, but Network Administrator worked fine. I had to enter settings in again. :D 

I did a lsmod, and found ndiswrapper still loaded. Not sure what to do with this. :confused: 
Anyone?

root@breezy:/home/andrew# lsmod | grep ndis
ndiswrapper           132296  0
usbcore               118396  4 ndiswrapper,ehci_hcd,ohci_hcd

...and to check what is running for the new card:

root@breezy:/home/andrew# lsmod | grep ath
ath_pci                79132  0
ath_rate_sample        17224  1 ath_pci
wlan                  143132  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148560  3 ath_pci,ath_rate_sample

---

### Post by queenorych on 2006-02-15
rmmod ndiswrapper
remove the ndiswrapper package.

you can also try to figure out why it is loading.  See if it is in /etc/modules

---

### Post by Sendervictorius on 2006-02-16
I've no idea why it was loading - not in /etc/modules - but it is not loading now, and no error messages, so that's ok. One last thing to do, and that is to change my firewall rules because the interface has changed from wlan0 to ath0.

Thanks for your help, queenorych.

---

