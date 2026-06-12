---
title: "Card Slot not working - Vista OK"
date: 2011-07-31
forum: Desktop Environments
---

### Post by Geffers on 2011-07-31
I have a dual boot HP laptop that has an SD/MMS/XD card slot as well as an Acer Aspire One netbook that has two card slots.

On my HP laptop the card slot works fine with Vista but is not recognised when I boot in to Ubuntu.

On my netbook the original supplied Linpus OS obviously recognised both slots, when I load Ubuntu only one slot is recognised.

Not a great inconvenience as I have a USB card reader for the HP and the Acer has two slots anyway but I would appreciate any ideas how to resolve this.

Geffers

---

### Post by Geffers on 2011-07-31
Further to my last no notification shows in /var/log/messages when the cards are inserted or removed.

Geffers

---

### Post by Geffers on 2011-07-31
> **Geffers said:**
> I have a dual boot HP laptop that has an SD/MMS/XD card slot as well as an Acer Aspire One netbook that has two card slots.

On my HP laptop the card slot works fine with Vista but is not recognised when I boot in to Ubuntu.

Geffers

Strangely, I have just booted in to my new Debian system working off a USB key and the card shows perfectly with the following line in the messages log.

> Jul 31 17:45:58 mercury kernel: [  177.599102] mmc0: new SDHC card at address 1234
Jul 31 17:45:59 mercury kernel: [  178.611315] mmcblk0: mmc0:1234 SA08G 7.40 GiB 
Jul 31 17:45:59 mercury kernel: [  178.611434]  mmcblk0: p1

I'm not sure what makes Linux recognise new hardware, my Ubuntu system works fine when new USB devices are inserted so I am thinking it may be a driver problem.

Any pointers appreciated.

Geffers


Geffers

---

### Post by Geffers on 2011-08-06
> **Geffers said:**
> Strangely, I have just booted in to my new Debian system working off a USB key and the card shows perfectly. 

Geffers

Booted my Debian system today and card doesn't show :(

Geffers

---

