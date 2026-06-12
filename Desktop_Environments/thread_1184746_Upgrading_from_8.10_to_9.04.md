---
title: "Upgrading from 8.10 to 9.04"
date: 2009-06-11
forum: Desktop Environments
---

### Post by metricspace on 2009-06-11
Hi, 

I've 8.10 installed and want to upgrade to 9.04 from a CD/DVD. Please guide.

I've setup my nvidia graphic card in 8.10 by trial and error. don't want to go again downloading drivers and getting my graphic card work for 9.04.

would be very good if someone can suggest me an upgrade from 9.04 CD/DVD, without me going for re-installation  of my graphic card drivers.

Thanks a bunch, forum members helped me earlier in getting me intall the  NVDIA drivers on 8.04.

Thanks,
Arif

---

### Post by balloooza on 2009-06-11
what nvidia do you have
```
lspci
```
will tell me, can you report that, and While you upgrade, I will keep the link to the file (it could be a legacy driver, I have had the same problems)

---

### Post by Therion on 2009-06-11
Download the Alternate Install CD.  Burn it to a CD and pop it in your drive.  Once the CD is read you will be prompted to upgrade from it.  You do NOT need to boot from the Alternate CD to do this.  Boot normally, insert CD, wait for the upgrade prompt.

---

### Post by metricspace on 2009-06-11
> **Therion said:**
> Download the Alternate Install CD.  Burn it to a CD and pop it in your drive.  Once the CD is read you will be prompted to upgrade from it.  You do NOT need to boot from the Alternate CD to do this.  Boot normally, insert CD, wait for the upgrade prompt.

my inet is not good to download a CD, I've got a free ubunut Disc of 9.04 from
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/), is there a way i can upgrade to 9.04 using this Disc.

would prefer a method where i need not have to re-install the NVIDIA dispaly drivers (proprietary) again after the upgrade.

Thanks a bunch for help,
metric.

---

### Post by Therion on 2009-06-11
> **metricspace said:**
> ... is there a way i can upgrade to 9.04 using this Disc.
No, you'll need to do a fresh install from that CD if you can't download the Alternate Install CD.

> **metricspace said:**
> would prefer a method where i need not have to re-install the NVIDIA dispaly drivers (proprietary) again after the upgrade.
Understood.  The Restricted Driver Manager SHOULD recognize, and install for you, the proper driver for your video card.  If it doesn't you could always use Envy instead.  

Install it by using the Termial:```
sudo apt-get install envyng-qt
```
Then run it from the Applications/System Tools menu.  Envy will determine the proper driver for your card, then download and install the proper restricted driver for it.

---

### Post by metricspace on 2009-06-11
Thanks for the help, I'll try to see if I can manage to get my hands on alternate CD 

metric

---

