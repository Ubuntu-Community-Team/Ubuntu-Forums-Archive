---
title: "Boot .iso from external drive"
date: 2009-03-21
forum: General Help
---

### Post by prem1er on 2009-03-21
I just bought a net book and I want a clean install of ubuntu on it.  I don't have a cd drive but I have and external with and .iso image.  Is there a way to just boot that directly from the drive?  Thanks

---

### Post by Bachstelze on 2009-03-21
Documentation on installing Ubuntu from a USB drive is [here]("https://help.ubuntu.com/community/Installation/FromUSBStick").

---

### Post by mb_webguy on 2009-03-22
You need to find out what sort of boot devices can be used by your BIOS.  When you next boot your computer, there should be a key combination to enter your BIOS setup.  Look for something along the lines of boot order or boot devices.  Hopefully, you'll see something about a USB device.  Make sure this is selected.

Now you said that you have an "external drive".  Do you mean an external optical disc drive, or just an optical storage drive?  If it's the former, then just burn the Ubuntu ISO to a disc, boot using the external disc drive, and you're good to go.  Otherwise, burn the ISO to a disc, then boot another computer from the disc.  Stick a USB flash drive (which doesn't have anything on it you want to keep) into the computer, and go to System->Administration->Create a USB Startup Disk.  This will create a LiveUSB that you can use to boot your netbook and install Ubuntu.

---

### Post by davo11 on 2009-03-22
if you have access to a windows computer download and use [UNetBootin]("http://sourceforge.net/project/showfiles.php?group_id=222386&package_id=268713&release_id=666365")(there is a version for linux but it did not work as well for me. the usb making is fairly self-explanatory from there.
or alternatively download [U810p.exe]("http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/")from this page. Then follow the instructions on the page.
Hope this helps.

---

### Post by prem1er on 2009-03-22
> **davo11 said:**
> if you have access to a windows computer download and use [UNetBootin]("http://sourceforge.net/project/showfiles.php?group_id=222386&package_id=268713&release_id=666365")(there is a version for linux but it did not work as well for me. the usb making is fairly self-explanatory from there.
or alternatively download [U810p.exe]("http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/")from this page. Then follow the instructions on the page.
Hope this helps.

Thanks everyone as usual.  Decided to get this program on a windows machine.  Works like a charm.

---

