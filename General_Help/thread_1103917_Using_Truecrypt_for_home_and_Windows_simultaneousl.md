---
title: "Using Truecrypt for /home and Windows simultaneously"
date: 2009-03-23
forum: General Help
---

### Post by MaximumFish on 2009-03-23
Hey everyone,

Here's an interesting question. I have Windows XP and Ubuntu 8.10 dual booting on my Asus N10J laptop. Currently both systems are encrypted (Windows using Truecrypt, Ubuntu using the built in system) but the hard drive is quite slow and the encryption layer on top makes it worse.

That got me thinking over the weekend, and I happened upon a curious solution that may or may not work...

My idea is to set up two 20GB partitions, one for Windows and one for Ubuntu, both of which will be unencrypted. Then the remainder of the disk will be made into a Truecrypt partition, formatted as NTFS or possibly FAT32.

In Windows I'll move the Documents and Settings (or at least My Documents) folder to the Truecrypt partition via registry tweaks and have TC auto-mount the partition on boot. It seems that it's possible to do a similar thing with Linux, as shown here: [http://notes.lokorin.org/2007/1/9/mounting-truecrypt-partitions-on-boot](http://notes.lokorin.org/2007/1/9/mounting-truecrypt-partitions-on-boot)

My question is though... Will using this partition for both systems screw one or the other up some how? Also, can Ubuntu use an NTFS or FAT32 filesystem for its /home location?

Finally, how would I go about moving /home to the TC partition once I'd got that set up?

Any thoughts or insight are much appreciated!

Thanks,

Max

---

### Post by avilella on 2009-04-05
If you have access to an ASUS N10J and have tried to run Linux, please take a moment to provide the DSDT information for the laptop in this link:

[https://bugs.launchpad.net/bugs/312756](https://bugs.launchpad.net/bugs/312756)

   1. Linux and Sony Vaio Z-series (intel/nvidia)
   2. Linux and Fujitsu Siemens Amilo XI 3650 (intel/nvidia)
   3. Linux and BenQ Joybook S42 (intel/nvidia)
   4. Linux and ASUS N10J (intel/nvidia)
   5. Linux and Dell Studio XPS 13 (nvidia/nvidia)
   6. Linux and ASUS Intros G71Gx (?/nvidia GeForce 260M)
   7. Linux and MSI GT628 (?/nvidia GeForce 160M)
   8. Linux and LG Xnote P510 Laptop (?/nvidia GeForce GT 130M)
   9. HP HDX 18t (?/nvidia GeForce GT 130M)
  10. Linux and Dell XPS M1730 (nvidia/nvidia)
  11. Linux and MSI EX630 (nvidia/nvidia)
  12. Toshiba Qosmio X305-Q706/Q708 (nvidia/nvidia -- 9400m + 2x9800m GTS)
  13. Acer Aspire 7530 (nvidia/nvidia -- 9100m + ?)
  14. Linux and Lenovo ThinkPad T500 (intel/ati)
  15. Linux and Lenovo ThinkPad T400 (intel/ati)
  16. Linux and ASUS M51Ta (intel/ati)
  17. Linux and Fujitsu-Siemens Amilo Sa 3650 (intel/ati)
  18. Linux and MSI PX211 12'' (intel/ati)
  19. Linux and HP Pavilion tx2500 (intel/ati)

DSDT is an acronym for Differentiated System Description Table. This table contains the Differentiated Definition Block, which supplies the information and configuration information about the base system. It is always inserted into the ACPI Namespace by the OS at boot time.

If you've got a laptop with a IGP and a hybrid Nvidia or ATi card, and you have tried to use Linux on it, you may have noticed that there are issues with the hybrid graphics setup. To help improve the Linux hybrid graphics support for this laptop, please attach your DSDT information to this Launchpad bug report specifying your laptop model:

[https://bugs.launchpad.net/bugs/312756](https://bugs.launchpad.net/bugs/312756)

To compile your DSDT information, install if you haven't already the acpidump and iasl tools:
sudo apt-get install acpidump iasl           # on Debian-based systems

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat

This will create a DSDT.dsl file that you can attach to the bug report. This information will allow the developers to fully implement the hybrid graphics features for Linux.

---

