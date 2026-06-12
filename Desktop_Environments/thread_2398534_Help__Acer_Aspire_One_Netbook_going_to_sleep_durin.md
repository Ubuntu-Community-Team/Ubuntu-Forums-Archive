---
title: "Help : Acer Aspire One Netbook going to sleep during boot,login and logout."
date: 2018-08-13
forum: Desktop Environments
---

### Post by applebuzz on 2018-08-13
**_[SIZE=4]*Problem now fixed, bios update sorted it out*[/SIZE]_**

Hello all, so here is my predicament (the technical details will follow).

I have a rather old netbook that I used to run lubuntu 14 (this version being upgraded from a previous lubuntu 12 install) on without any issues, however, I recently attempted to update it to 16 and my netbook developed the rather distressing habit of going to sleep during boot, upon logging in, and upon shutting down (looks like it happens during logout). I immediately grabbed a lubuntu 14 iso, tried did a clean install, but the problem was still there!

I've had a good search online and found a hacky fix (***now running Xubuntu 18***) that does work, but the tradeoff is I no longer know the status of my battery; a bit of a problem for a netbook that travels a lot!

I would deeply appreciate any help finding a better solution to this problem.


_**The Laptop (and its history)**_

Hardware Breakdown : ACER ASPIRE ONE, Model D159-1577, ram upgraded from 1GB to 2GB 6 years ago, keyboard replaced twice.


_**lshw dump**_
[https://paste.ubuntu.com/p/bHVqQgxh25/](https://paste.ubuntu.com/p/bHVqQgxh25/)


**_Notes on the problem and steps already taken_**

The problem is that during boot, the laptop will enter standby.  Once the login screen has appeared, attempting to log in will also cause the laptop to enter standby.  Finally, when logging out, the laptop will also enter standby.

In all three cases, pressing the power button resumes operations; though during the first hibernation (the one during boot) at least 10--15 seconds pass before the button press registers.

This is an issue that occours on all LTS variations of ubuntu (lubuntu, xubuntu both tested) from V14 onwards (tried 14, 16 and 18, all using latest iso, have run update and dist-upgrade on all); though a set up that upgrades from V13 to V14 does not manifest this issue.

Live USBS do not exhibit any of these issues, they only occour after installation.  Full reformatting and recreation of partitions does not solve.

A quick hack fix is to modify the grub file to disable the acpi

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

The side effect of this is that no battery meter is present during laptop operation (no issue when plugged in, but damn risky when traveling!)  Another odd effect is that my numlock is turned on when the login screen appears; and my numlock flashes on/off at the exact times when a hibernate would normally occour.

I did try

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_sleep=nonvs", and this appeared to work for a single boot, but the problem resumed the following boot. 

I've also tried modifying the lightdm hibernation permissions dealing with the lid, but no dice.


**_My current functioning GRUB_**

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off pnpbios=off pci=biosirq"
GRUB_CMDLINE_LINUX=""
```


_**Reference copy of dmesg AFTER hacky fix applied (no major errors)**_

[https://paste.ubuntu.com/p/wQpmtF6qrp/](https://paste.ubuntu.com/p/wQpmtF6qrp/)
[U][B]

Reference copy of dmesg before hacky fix applied (A lot of machine anger right there)

[/B][/U][https://paste.ubuntu.com/p/x6CrTxtM43/](https://paste.ubuntu.com/p/x6CrTxtM43/)

---

