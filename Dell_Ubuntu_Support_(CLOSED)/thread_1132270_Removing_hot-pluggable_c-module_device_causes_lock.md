---
title: "Removing hot-pluggable c-module device causes lockup on SX260"
date: 2009-04-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shinji257 on 2009-04-21
Any time I remove a c-module devices from my system it causes a complete lockup of the computer.  The device itself does not appear to be recognized as hot-pluggable but I am able to remove and swap while the computer is running on XP just fine.  Is there any fix to this?  I understand that the ultrabay devices for ibm thinkpads can be done.  They are very similar to the ones used in some older Dell Latitude laptops and my particular desktop model.

Ok.  I think I found a workaround.  This site gave me a heads up > [http://www.thinkwiki.org/wiki/How_to_hotswap_UltraBay_devices](http://www.thinkwiki.org/wiki/How_to_hotswap_UltraBay_devices)

I have a dvd burning installed so once I found the correct device node I ran the following to "eject" the device.  I had to do it as root though by typing 'sudo su' though as a standard sudo with the command didn't work.

echo 1 > /sys/class/scsi_device/1\:0\:0\:0/device/delete

I verified that it was ejected with dmesg and it reported "ata2.00: disabled".  Afterwards I was able to eject the device without the machine locking up.

Now then once you have a new device installed. I typed the following.

echo 0 0 0 > /sys/class/scsi_host/host1/scan

This will tell the system to rescan the device and you should confirm that the new device has loaded by checking that the device activity led flashes and dmesg should report it found.

For some reason I couldn't get a floppy running via hotplug swap but I am probably telling the wrong device to rescan.  I'm going to reboot with the floppy installed and see what comes up.

---

