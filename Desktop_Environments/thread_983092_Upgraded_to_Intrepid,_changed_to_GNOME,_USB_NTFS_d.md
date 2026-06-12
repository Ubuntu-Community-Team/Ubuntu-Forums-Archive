---
title: "Upgraded to Intrepid, changed to GNOME, USB NTFS drive no longer recognized"
date: 2008-11-15
forum: Desktop Environments
---

### Post by jr0dy on 2008-11-15
I'm relatively new to the Linux platform.  I've been using KDE for awhile on Hardy Heron and just performed a clean install of Intrepid Ibex and opted for GNOME this time based on many, many recommendations from friends.  I'm starting to regret that decision.

Whereas KDE recognized and automounted my external NTFS USB hard drive, GNOME does not recognize its presence whatsoever.  My FAT-formatted flash drives work fine.  My other USB 1.1/2.0 devices work fine.  The hard drive is detected and works flawlessly when I boot into my WinXP partition (which I was hoping not to have to boot into anymore :) ).  I just recently installed 8.10 with GNOME on another computer and that computer does not recognize the drive, either, so based on that it appears this is GNOME-specific.

fdisk -l and lsusb turn up absolutely nothing in regards to the drive, so it's not just a problem in regards to the mounting but in recognizing it as being there.

I had some troubles after the initial install with some internal NTFS SATA drives where the system wouldn't boot to the GNOME login if anything other than just the system drive was plugged in at boot, but that seems to have been resolved, yet leads me to believe they may be conflicting somehow.

I really want to stay with GNOME, but this is driving me insane.  I've been going through forums for probably a total of 5 hours on this and I am looking to either put it to rest or switch back to KDE.  For all of you GNOMEiacs out there who would want to keep me from switching back, please help me.

---

### Post by jr0dy on 2008-11-19
Please? :)

---

### Post by akudewan on 2008-11-19
Maybe some log files will tell whats going on:
```

dmesg | tail
tail /var/log/messages
tail /var/log/syslog

```

Doesn't seem to be a Gnome issue if you ask me, (since lsusb is also turning up nothing).

Btw, you can keep Gnome and KDE both installed, if you have enough disk space. You can select the environment when you login.

---

### Post by win4thebin on 2008-11-19
First of all the usb thumbdrive should be formated with fat32. but if you want kde back try opening terminal and typing *sudo apt-get install kubuntu-desktop* (note: this uses between 200 mb and 700 mb of download.

---

### Post by jr0dy on 2008-11-26
Thank you very much for responding - I was starting to lose faith :).  I'll run the logs when I get home tonight and post the results.

One other item I should at least mention - I'm running a dual core AMD processor (about 3 years old now, I want to say it was a 2.0 GHz Manchester chip, but not sure off-hand) but due to some problems finding 64-bit versions for certain applications I decided to just install an x86 version of Ubuntu.  I may return back to 64-bit as I've noticed a significant loss in processing power.

Furthermore, back in my Windows days, I discovered my motherboard has a major flaw, in that when you run an AMD2 chip on it, it causes major instability for USB 2.0 devices, so I had to drop the on-board USB BIOS setup down to 1.1 support only and install a USB 2.0 PCI card for my 2.0 devices.

Although both items are seemingly irrelevent, I have found zero to no documentation on this issue elsewhere so I figured the more info the better.

---

