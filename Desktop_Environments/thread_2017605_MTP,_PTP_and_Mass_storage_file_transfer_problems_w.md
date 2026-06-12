---
title: "MTP, PTP and Mass storage: file transfer problems with Android"
date: 2012-07-05
forum: Desktop Environments
---

### Post by dargaud on 2012-07-05
Hello all,
I have a Samsung Galaxy SII Android phone and all the methods of file transfer from the computer have problems. 

I used to use MassSorage by default in Android 2.3, but the default is now gone with the 4.0 upgrade and you have to search for it in the settings every time (OK, that's not Ubuntu's problem). And when using Mass Storage, the file transfers to the phone start off well, but after about 400Mb (probably some buffer), they slow down to a crawl and the PC becomes completely unresponsive for dozens of seconds at a time, sometimes 2 full minutes, then reacts for a few seconds, then locks up again. Once the transfer is finished (taking hours), the PC works fine again. Using rsync with rate limiting options works perfectly but is very awkward since you can't transfer individual files with rsync.

I have no idea what MTP/PTP are, but when I try to use them, the PC opens dolphin with an empty camera:/Samsung GT-P7510/Galaxy Tab 10.1/S2/GT-N7000/Galaxy Nexus@usb:006,002/ and I have no idea what to do with it. This is probably relevant:
```
$ dmesg
[  372.722549] kio_kamera[5191]: segfault at 29c04920 ip 00007f8bfdf208d3 sp 00007fff1278e2e0 error 4 in libc-2.15.so[7f8bfdee5000+1b3000]
[  375.284566] kio_kamera[5203]: segfault at 29c04840 ip 00007f8bfdf208d3 sp 00007fff1278e2e0 error 4 in libc-2.15.so[7f8bfdee5000+1b3000]
[  375.414126] kio_kamera[5206]: segfault at 29c049d0 ip 00007f8bfdf208d3 sp 00007fff1278e460 error 4 in libc-2.15.so[7f8bfdee5000+1b3000]

```

PTP is the same and doesn't work also: camera:/USB PTP Class Camera@usb:006,003/ is empty
```
[  904.921998] usb 6-1: USB disconnect, device number 2
[  905.288105] usb 2-4: new high-speed USB device number 9 using ehci_hcd
[  905.428043] usb 2-4: device descriptor read/64, error -71
[  905.668074] usb 2-4: device descriptor read/64, error -71
[  905.884102] usb 2-4: new high-speed USB device number 10 using ehci_hcd
[  906.024120] usb 2-4: device descriptor read/64, error -71
[  906.264058] usb 2-4: device descriptor read/64, error -71
[  906.480174] usb 2-4: new high-speed USB device number 11 using ehci_hcd
[  906.904161] usb 2-4: device not accepting address 11, error -71
[  907.016084] usb 2-4: new high-speed USB device number 12 using ehci_hcd
[  907.440070] usb 2-4: device not accepting address 12, error -71
[  907.440106] hub 2-0:1.0: unable to enumerate USB device on port 4
[  907.772110] usb 6-1: new full-speed USB device number 3 using ohci_hcd
[  907.931417] usb 6-1: not running at top speed; connect to a high speed hub

```

---

### Post by Redblade20XX on 2012-07-05
I've heard of problem with the galaxy and mtp too. But still take a look here for an mtp guide through the terminal.

[https://wiki.archlinux.org/index.php/Mtp](https://wiki.archlinux.org/index.php/Mtp)

If you want a gui method, try installing gmtp.
```
sudo apt-get install gmtp
```

If the gui method doesn't work, try out the terminal method.

- Red

---

### Post by dargaud on 2012-07-06
Thanks for the tip. Here's more background but I didn't go much further:
```
$ mtp-detect 
libmtp version: 1.1.3

Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung GT-P7310/P7510/N7000/I9100/Galaxy Tab 7.7/10.1/S2/Nexus/Note.
   Found 1 device(s):
   Samsung: GT-P7310/P7510/N7000/I9100/Galaxy Tab 7.7/10.1/S2/Nexus/Note (04e8:6860) @ bus 2, dev 10
Attempting to connect device(s)
PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
LIBMTP PANIC: failed to open session on second attempt
Unable to open raw device 0
OK.

$ gmtp
Device 0 (VID=04e8 and PID=6860) is a Samsung GT-P7310/P7510/N7000/I9100/Galaxy Tab 7.7/10.1/S2/Nexus/Note.
PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
LIBMTP PANIC: failed to open session on second attempt
Detect: Unable to open raw device?
LIBMTP PANIC: Trying to dump the error stack of a NULL device!
LIBMTP PANIC: Trying to clear the error stack of a NULL device!


$ mtpfs -o allow_other /media/mymtp
$  ll /media
ls: cannot access /media/mymtp: Transport endpoint is not connected
d?????????  ? ?       ?          ?            ? mymtp/

```

---

### Post by dargaud on 2012-07-08
From reading various messages about this very subject it appears that:
- The Samsung MTP implementation is highly specific
- Recompiling the latest libmtp seems to help some people (haven't tried)
- There may be something wrong with my usb cable and/or USB port on that machine because another machine doesn't have hang problems in Mass Storage mode.

---

