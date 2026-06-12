---
title: "Updating BIOS /UEFI on ubuntu only machines"
date: 2020-04-21
forum: Desktop Environments
---

### Post by steve.clay on 2020-04-21
Hi, I am thinking of buying a Dell Inspiron 3471. It comes with a trial version of Windows but what I really want to do is completely erase the software on it and replace it with ubuntu. However i recently had a problem with an old acer m3985 which I have now, which was that it needed a BIOS / UEFI update and the only software available on the acer site was really old and only runs on Windows. I did try applying this update using wine but it didn't work.

So my question is: is it possible to update UEFI when it is necessary on modern machines even if they only have ubuntu on them? Or is it better to have a small partition with some DOS or Windows product purely for no other reason that to be able to apply these updates when required?

---

### Post by oldfred on 2020-04-21
How new?
Fwupd 1.4 brings with it many improvements  April 20, 2020
[https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-1.4-Released](https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-1.4-Released)
UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
fwupx64.efi
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

But many systems have multiple ways to update UEFI. From Windows, from DOS bootable flash drive, and directly from UEFI reading a FAT32 partition, either flash drive or on HDD,SSD. I make my ESP - efi system partition a bit larger so I can use that.

---

### Post by hk42 on 2020-04-22
Completely removing an OS from a computer is a bad idea.
HDD space has never been so cheap.
There are a few Android applications  I would like to use on Intel devices.

---

### Post by CatKiller on 2020-04-22
> **steve.clay said:**
> So my question is: is it possible to update UEFI when it is necessary on modern machines even if they only have ubuntu on them?

Yes. 

In the olden days (when BIOS was the only game in town) you needed a special application (generally a DOS application) to write the new firmware to the appropriate addresses, since the BIOS was too limited to do so itself. You'd boot up a DOS floppy and run the special application and it would copy your file to the chip on the motherboard that holds the BIOS.

Nobody uses BIOS any more. It's been replaced by UEFI, which is much more capable in general and can run its own programs. You feed it the new file, either on a USB stick or from somewhere that the UEFI can read from like the EFI System Partition, and it handles the rest itself. 

No one should ever update the UEFI from within Windows. Just the thought of it gives be chills. 

In addition, firmware can be loaded on the fly - one of the advantages that UEFI has over the old BIOS. That can be for things like graphic devices or network devices, or for lower-level things on the motherboard. Under Linux the mechanism is fwupd (firmware update daemon) in conjunction with LVFS (Linux Vendor Firmware Service). The manufacturer passes their firmware to LVFS, which is a clearing house for getting that to distros and end users, and then the firmware gets loaded at boot time by fwupd without having to permanently flash it to a device. Some manufacturers are better than others at getting their firmware onto LVFS.

Dell are good for Linux support (although I have no experience of that particular model) since they sell machines with Linux on. By upstreaming their drivers and getting any necessary firmware onto LVFS - as well as using Linux-friendly hardware in the first place - they no longer have to maintain or distribute it directly themselves.

---

### Post by rbmorse on 2020-04-22
Using the EFI partition for UEFI updates on machines that will read the update file from a fat32 formatted partition is a clever idea.  Thanks for the hint.

---

### Post by oldfred on 2020-04-22
The only hassle with using the ESP for UEFI updates, is permissions.
Ubuntu used to use defaults in fstab to mount it back with 14.04 & before. But changed to use 0077 which is no permission. I assume for security reasons. If you run Boot-Repair it changes to defaults, I currently change to defaults, but may change back to the 0077 and use live installer to save into ESP.
Example, but I also found I have to reboot. From fstab:
```
#UUID=D966-440A  /boot/efi       vfat    umask=0077      0       1
UUID=D966-440A  /boot/efi       vfat    defaults      0       1

```
After any edit of fstab, run this to make sure not errors. But it does not seem to remount ESP with new permissions until you reboot.
sudo mount -a

---

### Post by CatKiller on 2020-04-22
> **oldfred said:**
> The only hassle with using the ESP for UEFI updates, is permissions.

The couple of times I've done it that way, rather than using a thumb drive (for the one computer that's hidden behind my TV), I've pulled up an actual root shell and that's worked fine with however it's configured. Obviously you need to know what you're doing and be paying attention when you've got a root shell going, but you need both of those things when you're updating the UEFI anyway.

---

