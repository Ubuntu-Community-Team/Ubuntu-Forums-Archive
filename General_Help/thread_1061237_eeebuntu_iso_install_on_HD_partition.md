---
title: "eeebuntu iso install on HD partition"
date: 2009-02-05
forum: General Help
---

### Post by tranquito on 2009-02-05
Hi there, a friend of mine recently got a asus eeePC with Xandros pre-istalled which she hates. I downloaded the iso for Ubuntu eee but I don't have a memory-stck. Is ther a way to boot an ISO file, from partitioned space on an external HD; so as to have a "Live Partition" of sorts. If ubuntu can live run from a usb stick then why not a HD partition?

---

### Post by dcstar on 2009-02-05
> **tranquito said:**
> Hi there, a friend of mine recently got a asus eeePC with Xandros pre-istalled which she hates. I downloaded the iso for Ubuntu eee but I don't have a memory-stck. Is ther a way to boot an ISO file, from partitioned space on an external HD; so as to have a "Live Partition" of sorts. If ubuntu can live run from a usb stick then why not a HD partition?

An iso is a CD image, burn it to a CD using the exact same instructions as for every other iso image.

---

### Post by tranquito on 2009-02-05
> **dcstar said:**
> An iso is a CD image, burn it to a CD using the exact same instructions as for every other iso image.


EEEpcs don't have a cd drive so I can't install that way. Burning isos to mem sticks is possible with the usb maker on Intrepid, but I was wondering if it was possible on a HD partition instead of a stick.

---

### Post by mpsii on 2009-02-05
You could try UNetBootin

---

### Post by dcstar on 2009-02-05
> **tranquito said:**
> EEEpcs don't have a cd drive so I can't install that way. Burning isos to mem sticks is possible with the usb maker on Intrepid, but I was wondering if it was possible on a HD partition instead of a stick.

You can install the files onto any sort of USB storage device, a stick or a drive, it makes no difference.

---

### Post by warp99 on 2009-02-05
Download UNetbootin either for Linux or Windows so you can write the ISO image to a flash drive. Once you have a bootable flash device insert the drive and reboot the computer. At the eee start up window press "esc", then choose the flash device with the image. From there just install as you would with a CD.

UNetbootin can be downloaded here:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Edit:

UNetbootin allows for a "frugal install" from a HD partition.

---

### Post by tranquito on 2009-02-06
sounds great.*I'll try it out and report back Thanks.

---

### Post by Myke Greywolf on 2009-02-06
You can also use the same method with any SD card. The EeePC has a SD card slot, and you can boot from it.

---

### Post by tranquito on 2009-02-06
Doesn't boot on EEEpc at all. I switched the BIOS settings to verbose boot but i still just get a flashing cursor. Whats up? The partition is definatly bootable after using Unetbootn. I tried booting it from my desktop and another laptop with no issues. Any ideas? I think the problem might be with the xandros bootloader but i'm not sure what to do next.

---

### Post by tranquito on 2009-02-06
> **Myke Greywolf said:**
> You can also use the same method with any SD card. The EeePC has a SD card slot, and you can boot from it.

If the HD boot doesn't work out i'll keep this in mind. THX

---

### Post by MysticGold04 on 2009-02-06
I made a Ubuntu USB stick with an 8.10 desktop machine (Make a Bootable USB Stick) to install 8.10 on my EeePC.  USB sticks are very cheap now-a-days, just go pick one up. a 1GB one should be enough to fit the CD on there. 

When finished with that process, with the USB stick in the USB port, reboot the Eee and hit 'Esc' to display the boot menu... you should be able to boot off of the USB stick and install away... Note: this will only work if you are running 8.10.  If you are running 8.04 I believe you will have to use UNetBootin.

EDIT: you can do the same thing with the eeebuntu .iso though Ubuntu 8.10 as well.

---

