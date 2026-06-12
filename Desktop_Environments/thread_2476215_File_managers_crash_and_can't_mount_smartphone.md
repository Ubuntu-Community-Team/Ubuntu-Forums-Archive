---
title: "File managers crash and can't mount smartphone"
date: 2022-06-20
forum: Desktop Environments
---

### Post by Jonners59 on 2022-06-20
```
Linux BaroniPC 5.15.0-37-generic #39-Ubuntu SMP Wed Jun 1 19:16:45 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
```


I have been having some issues lately and decided today was the day to resolve them.

1.  I found that recently my Android smartphone was not mounting when I connected it to my PC.  The phone has USB Debugging allowed and I get the request to choose file share, photo or none, but it does not appear on my PC in Thumar or Nautilus, and I get no pop-up announcing its connection.
In a terminal, I get ```
$ lsusb
Bus 002 Device 008: ID 2717:ff48 Xiaomi Inc. Mi/Redmi series (MTP + ADB)
Bus 002 Device 006: ID 062a:4102 MosArt Semiconductor Corp. Wireless Mouse
Bus 002 Device 005: ID 05a3:9331 ARC International Camera
Bus 002 Device 009: ID 2109:8817 VIA Labs, Inc. USB Billboard Device   
Bus 002 Device 004: ID 2109:2817 VIA Labs, Inc. USB2.0 Hub             
Bus 002 Device 003: ID 06a3:0d60 Saitek PLC Saitek ST290 Pro
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0080:a001 Unknown JMS578 based SATA bridge
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 047f:c016 Plantronics, Inc. Plantronics C510-M
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

So, it is listed - 1st item [PHP]Xiaomi Inc. Mi/Redmi series (MTP + ADB)[/PHP]

2. Also Thumar has been crashing after a few minutes.  I'll open it and may be able to open a document, search, or copy a file, and then it would crash.  So I would switch to Nautilus, opening by typing nautilus in a terminal.  All was fine until I tried to fix Thumar today.  Now neither work.  When I type nautilus in the terminal I get;-
```
nautilus
Initializing nautilus-image-converter extension
Traceback (most recent call last):
  File "/usr/share/nautilus-python/extensions/nautilus-hide.py", line 20, in <module>
    from gettext import ngettext, locale, bindtextdomain, textdomain
ImportError: cannot import name 'locale' from 'gettext' (/usr/lib/python3.10/gettext.py)
Initializing Nextcloud-client-nautilus extension
Using python version sys.version_info(major=3, minor=10, micro=4, releaselevel='final', serial=0)
Could not connect to unix socket /run/user/1000/Nextcloud/socket. [Errno 2] No such file or directory
Initializing nautilus-dropbox 2019.02.14
Initializing nautilus-ideviceinfo extension
sys:1: Warning: Two different plugins tried to register 'NautilusDiscBurn'.
sys:1: Warning: g_type_add_interface_dynamic: assertion 'G_TYPE_IS_INSTANTIATABLE (instance_type)' failed
nautilus-wipe-Message: 11:30:16.333: Initializing
**
ERROR:../src/nautilus-file.c:611:nautilus_file_new_from_filename: assertion failed: (filename[0] != '\0')
Bail out! ERROR:../src/nautilus-file.c:611:nautilus_file_new_from_filename: assertion failed: (filename[0] != '\0')
Aborted (core dumped)

```

---

### Post by TheFu on 2022-06-20
Phones don't actually mount. They have two protocols - MTP and PTP that are used instead.  Typically, Linux file managers would use MTP, so ensure that is enabled in the phone.

Specific support for the variant of MTP on your phone could be the issue.
Since the phone is being recognized, it seems the udev rule for it is there.

I only have 3 ideas.  
Try a different USB cable. Sometimes cables that worked before go bad.
Try using adb directory to access the storage. This is cumbersome, I'm sorry to say, but if adb doesn't work, then there's little chance that any file manager will work too.
Try turning off usb debugging. Seems that with some devices, this interferes with MTP access.

[https://wiki.debian.org/mtp](https://wiki.debian.org/mtp) has some more ideas.  Seems that most of the time, the issue is a bad USB cable. They recommend installing **gmtp** and trying it.

If you really want to mount the storage, there is a FUSE tool, mtpfs that can be installed to mount the storage. Just like davfs or sshfs, then we can run scripts from our Linux systems inside the mounted storage for file processing directly.  Hummmm. I wonder if that would be faster than the GUI MTP access I've seen, which is terribly slow.  Even if just pushing files over using rsync, I can see where mtpfs would be extremely useful.

Good question that helped me do a bit of research and learn some stuff. Thanks.

---

### Post by Jonners59 on 2022-06-20
Thank you "TheFu",
> **TheFu said:**
> Phones don't actually mount. They have two protocols - MTP and PTP that are used instead.  Typically, Linux file managers would use MTP, so ensure that is enabled in the phone.

Specific support for the variant of MTP on your phone could be the issue.
Since the phone is being recognized, it seems the udev rule for it is there.

I only have 3 ideas.  
Noted.

> **TheFu said:**
> Try a different USB cable. Sometimes cables that worked before go bad.   Noted and I agree.  I have just ordered a new one and shall try that before any other steps.

> **TheFu said:**
> Try using adb directory to access the storage. This is cumbersome, I'm sorry to say, but if adb doesn't work, then there's little chance that any file manager will work too.  I just tried to install adb and it says it is already installed.  How would I find/use it?  It's not in the apps.  I have a feeling that you'll come back and say it's a silly question.  :-D

> **TheFu said:**
> Try turning off usb debugging. Seems that with some devices, this interferes with MTP access.  Had already done that.  Actually, I found that it had switched off and then after turning it on it made no difference.

[URL="https://wiki.debian.org/mtp"]> **TheFu said:**
> https://wiki.debian.org/mtp[/URL] has some more ideas.  Seems that most of the time, the issue is a bad USB cable. They recommend installing **gmtp** and trying it.  Tried that.  Just seems to freeze.  Click "Connect" and nothing happens and in the terminal it states:

```
Error 2: PTP Layer error 02ff: obj2file: call to ptp_mtp_getobjectpropssupported() failed.
Error 2: Error 02ff: PTP I/O Error
Error 2: PTP Layer error 02ff: obj2file: call to ptp_mtp_getobjectpropssupported() failed.
Error 2: Error 02ff: PTP I/O Error
ERROR: Could not close session!
inep: usb_get_endpoint_status(): No such device
outep: usb_get_endpoint_status(): No such device
Detect: No raw devices found.

```

> **TheFu said:**
> If you really want to mount the storage, there is a FUSE tool, mtpfs that can be installed to mount the storage. Just like davfs or sshfs, then we can run scripts from our Linux systems inside the mounted storage for file processing directly.  Hummmm. I wonder if that would be faster than the GUI MTP access I've seen, which is terribly slow.  Even if just pushing files over using rsync, I can see where mtpfs would be extremely useful.

Good question that helped me do a bit of research and learn some stuff. Thanks.  Ohh, have that....  Out of my league.

SO new cable 1st, then open to ideas.

---

### Post by ActionParsnip on 2022-06-21
If the device is Android based then you can use AndFTP to connect to the Ubuntu system via SFTP (you'll need openssh-server installed). You can then send your files over the network. No wires needed

---

### Post by TheFu on 2022-06-21
> **ActionParsnip said:**
> If the device is Android based then you can use AndFTP to connect to the Ubuntu system via SFTP (you'll need openssh-server installed). You can then send your files over the network. No wires needed

+1.

Excellent point.  There are many ways, but sftp is probably the easiest and most secure method.  I use sftp sometimes for android, but also use my nextcloud server on my LAN to sync files between mainly android and the server.

But not all USB cables are great and fully support the standards.  Also, with devices we charge daily, the microUSB/USBc ports do wear out just from use of the years, so transferring files using a network ----- or just pulling the 2nd microSD card out and inserting it into a laptop to copy files will save some breakage of the phone's USB port.  Once that port breaks, the phone is worthless (cannot be charged).

---

### Post by Jonners59 on 2022-06-21
Dunno.  I have for decades just plugged the phone in and it worked.  It allowed me to move files about, delete, create directories etc as if it were part of the PC, Laptop etc.  I have used apps on the phone that I can find on the LAN to access the files, but it's not as nice.  It is odd that what is essentially a Linux machine (Android) work seamlessly with Windows and OX, yet with a Linux has issues/more problematic.

Anyway, new cable arrived and made no difference.  I can find the phone in the list and I can connect to it using gMTP, though when that connects it is empty.  I always and still want and expect to find my device in my File manager.  Why does it now show any more and how do I get it back...?

---

### Post by TheFu on 2022-06-21
If it isn't clear, we don't know what happened.
We are providing ideas and workarounds.

sftp is built-into Linux file managers usually.  I use a URL with sftp://nexux4/ and type in my credentials. 
```
$ ping nexus4
PING nexus4.mylan.lan (10.1.0.98) 56(84) bytes of data.
```

Plus, since my wifi stuff is on a different LAN from trusted desktops/laptops (FBI recommends this), going from the phone into the trusted LAN isn't really possible.  Well, it is, but only because I run a VPN server with ACLs that allows specific access from specific VPN clients into specific servers on the trusted LAN.

 "nexus4" is in my local DNS to resolve to an IP, but you can use the IP address.  DHCP reservations to the phone gets the same IP every time on your LAN will make that easier.  In a file manager, for my nexus4, the URL would be sftp://10.1.0.98/  I'd have to run an sftp-server on the phone.

Yes, it should work the old way over MTP using a USB cable, but that isn't working.  To troubleshoot that, I'd connect the USB-phone to the computer and check the system logs and dmesg to see if anything is clearly wrong. Then, based on any related errors, I'd plug those exact errors into web--search tools.  If there aren't any log entries, then I'd use lsusb, with some options, to get the specific device ID and see what udev (that's a systemd subsystem) is doing for that device.  You've already done the lsusb.  A result for that is:
[https://askubuntu.com/questions/956788/gnome-in-ubuntu-is-unable-to-recognise-android-phone-connected-to-pc](https://askubuntu.com/questions/956788/gnome-in-ubuntu-is-unable-to-recognise-android-phone-connected-to-pc)  But it is old and before the device was recognized in the huge USB database.  There are a few settings in that link, but I doubt they will be helpful.
[https://www.reddit.com/r/linuxquestions/comments/g6rvah/dolphin_cant_access_the_phone_via_mtp_majority_of/](https://www.reddit.com/r/linuxquestions/comments/g6rvah/dolphin_cant_access_the_phone_via_mtp_majority_of/) with some crazy ideas to try.

"The only constant is change".  That's life.

---

