---
title: "USB Flash Drive, Ubuntu: Yes, Windows:No, Why?"
date: 2009-02-11
forum: General Help
---

### Post by diskmaster23 on 2009-02-11
I am currently running Ubuntu 8.10 on my IBM Thinkpad T40 and I love it. I've been doing this for almost a year now and it has been however a rocky road, but a good experience. Some of my favorite features is the add/remove of applications, easy upgrades, pidgin (which isn't Ubuntu, but still a nice program), Compiz (only if I can find a way of using the superkey, IBM T40 doesn't have a superkey), and getting better flash player performance (sometimes using flash applications takes up my whole CPU, seems a little excessive) Anyways...

I have myself a 512MB usb flash drive that was working up till I used RSync. It does work on my IBM T40, but I have not been able to get it working in my desktop Ubuntu 8.04,Windows XP SP3, Vista, and Mac OS X. I have no idea why.

Windows recognizes that it is a USB device, but I never get beyond the "Unknown Device".

Mac just doesn't seem to respond at all. I didn't get a chance to really take a look at that.

My desktop Ubuntu doesn't even recognize it in lsusb. My laptop Ubuntu says "Bus 003 Device 012: ID 0457:0151 Silicon Integrated Systems Corp. Super Flash 1GB / GXT  64MB Flash Drive" but what doesn't makes sense to me is...it is a 512mb drive.

I have tried reformatting the USB drive in FAT16 and FAT32 with no difference in the results.

I have also tried many other different ports on the various different computers.

It would be nice to be able to use this USB drive on other machines.

Please help.

---

### Post by cariboo on 2009-02-11
Formatting Fat16 and Fat32 using gparted doesn't work very well in my experience. When I need to reformat a thumb drive, I always use Windows.

Jim

---

### Post by diskmaster23 on 2009-02-12
I would reformat it in windows, but I cannot even get past the "Unknown Device". Any suggestions?

---

### Post by mc4man on 2009-02-12
You could try this. Insert the drive in the laptop that it works in (thinkpad ?) and if it mounts unmount it.
Then I'm assuming you have a partition editor installed (gparted.

Delete the partition and leave the whole drive as unallocated space, probably about 470Mb. Then remove the drive and try to partition/format it in one of your other boxes (windows or your desktop 8.04, myself I've never had any issue with vfat partitioning with gparted

If you were to put a flash drive with no partitions on it in your 8.04 desktop, while nothing would happen (nothing to mount) you should be able to see it with 
sudo lshw -C disk

---

### Post by diskmaster23 on 2009-02-15
I tried what you said to do, and I couldn't even get the 8.04 to pick up under lsusb. I am not sure what to do about this. I  suppose the flash drive is dead except to my 8.10 computer?

---

### Post by diskmaster23 on 2009-02-16
Bump...........

---

### Post by geirha on 2009-02-16
On the ubuntu desktop. Insert the drive, then wait some 30 seconds or so to give it time to try to detect it, then run in a terminal ```
dmesg
``` Do you see any error messages?

---

### Post by diskmaster23 on 2009-02-17
```
[220992.934484] usb 3-3: new high speed USB device using ehci_hcd and address 11
[220993.046475] usb 3-3: device descriptor read/64, error -71
[220993.262462] usb 3-3: device descriptor read/64, error -71
[220993.478445] usb 3-3: new high speed USB device using ehci_hcd and address 12
[220993.590436] usb 3-3: device descriptor read/64, error -71
[220993.806420] usb 3-3: device descriptor read/64, error -71
[220994.022404] usb 3-3: new high speed USB device using ehci_hcd and address 13
[220994.430377] usb 3-3: device not accepting address 13, error -71
[220994.542367] usb 3-3: new high speed USB device using ehci_hcd and address 14
[220994.950337] usb 3-3: device not accepting address 14, error -71

```

That is what showed up on my 8.04 desktop.

---

### Post by dcstar on 2009-02-17
> **diskmaster23 said:**
> ......
I have myself a 512MB usb flash drive that was working up till I used RSync. **It does work on my IBM T40**, but I have not been able to get it working in my desktop Ubuntu 8.04,Windows XP SP3, Vista, and Mac OS X. I have no idea why.

Windows recognizes that it is a USB device, but I never get beyond the "Unknown Device".

Mac just doesn't seem to respond at all. I didn't get a chance to really take a look at that.

My desktop Ubuntu doesn't even recognize it in lsusb. My laptop Ubuntu says "Bus 003 Device 012: ID 0457:0151 Silicon Integrated Systems Corp. Super Flash 1GB / GXT  64MB Flash Drive" but what doesn't makes sense to .......

Old USB devices can be problematic, part of it may have well died as these things only have a finite life. It may be better to spend $10 and get a new 2GB drive.......

---

### Post by geirha on 2009-02-18
Does running ```
sudo modprobe -r ehci_hcd
``` as explained at [https://answers.launchpad.net/ubuntu/+question/4272](https://answers.launchpad.net/ubuntu/+question/4272) make it work on your desktop?

---

### Post by diskmaster23 on 2009-02-18
> **geirha said:**
> Does running ```
sudo modprobe -r ehci_hcd
``` as explained at [https://answers.launchpad.net/ubuntu/+question/4272](https://answers.launchpad.net/ubuntu/+question/4272) make it work on your desktop?

I ran sudo modprobe -r ehci_hcd, and it does work. But what do I do next? I was able to access my drive, but it still doesn't solve the problem. That is no good when it comes to other operating systems. The last post in the article talks about that as well (at least trying to access other drives).

Do I really have a bad USB drive? Did RSync kill it?

Thank you for the suggestions.

---

### Post by diskmaster23 on 2009-03-02
:::Bump:::

---

