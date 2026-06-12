---
title: "a few problems"
date: 2008-12-15
forum: General Help
---

### Post by inxygnuu on 2008-12-15
Hello, I am using Ubuntu 8.10, and I have a few problems, which always will result in me doing a cycle: I install Ubuntu, and once I get Vista working, I use that (because Ubuntu gets buggy after a while, don't know why) then I delete Ubuntu, then vista crashes, reinstall Ubuntu, and cycle repeats... Not this time :twisted:

Here are my problems:
1 Usb wont mount [problem described here]("http://ubuntuforums.org/showthread.php?t=1009597")
2 i have to hold a button when the orange thing goes back and forth
3 Webcam wont work (I tried cheese, it worked once, but now it only shows a blank screen)

Stop the cycle,
3v4n

---

### Post by cmnorton on 2008-12-16
How is Ubuntu too buggy? What problems occur? Perhaps, you could list one or two (related) problems per post.

This link

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

should be able to help you on dual-boot problems.

---

### Post by inxygnuu on 2008-12-16
> **cmnorton said:**
> How is Ubuntu too buggy? What problems occur? Perhaps, you could list one or two (related) problems per post.

This link

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

should be able to help you on dual-boot problems.

I am on Vista as I type this. I just need some bugs fixed. My last installation, *shivers* The Ethernet wouldn't work without a wireless adapter plugged in... I just need the 3 problems described in my first post solved.

---

### Post by inxygnuu on 2008-12-17
bumpity bump... :( ):P

---

### Post by nixscripter on 2008-12-19
Let me see if I can take a shot at one and two.

1. When you mount the USB drive and get the error, is the device recognized by the system? If you look at **/var/log/messages**, you should see something like this:

```

[15365.468000] usb-storage: device found at 2
[15365.468000] usb-storage: waiting for device to settle before scanning
[15365.468000] usbcore: registered new interface driver usb-storage
[15365.468000] USB Mass Storage support registered.
[15370.468000] usb-storage: device scan complete
[15370.468000] scsi 5:0:0:0: Direct-Access     **Brand-make-model**      0000 PQ: 0 ANSI: 0
[15370.472000] sd 5:0:0:0: [sdb] XXXXXXXXXXX 512-byte hardware sectors (XXXXXX MB)
[15370.472000] sd 5:0:0:0: [sdb] Write Protect is off
[15370.472000] sd 5:0:0:0: [sdb] Mode Sense: 27 00 00 00
[15370.472000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[15370.472000]  sdb: [mac] sdb1 sdb2 sdb3 sdb4
[15370.480000] sd 5:0:0:0: [COLOR="Red"][sdb][/COLOR] Attached SCSI disk
[15370.480000] sd 5:0:0:0: Attached scsi generic sg2 type 0

```

In this case, the device attached as **/dev/sdb**. 

2. While Ubuntu is booting, try hitting Cntl-F1 to see if there are any messages that might explain the problem.

---

### Post by inxygnuu on 2008-12-19
> **nixscripter said:**
> Let me see if I can take a shot at one and two.

1. When you mount the USB drive and get the error, is the device recognized by the system? If you look at **/var/log/messages**, you should see something like this:

```

[15365.468000] usb-storage: device found at 2
[15365.468000] usb-storage: waiting for device to settle before scanning
[15365.468000] usbcore: registered new interface driver usb-storage
[15365.468000] USB Mass Storage support registered.
[15370.468000] usb-storage: device scan complete
[15370.468000] scsi 5:0:0:0: Direct-Access     **Brand-make-model**      0000 PQ: 0 ANSI: 0
[15370.472000] sd 5:0:0:0: [sdb] XXXXXXXXXXX 512-byte hardware sectors (XXXXXX MB)
[15370.472000] sd 5:0:0:0: [sdb] Write Protect is off
[15370.472000] sd 5:0:0:0: [sdb] Mode Sense: 27 00 00 00
[15370.472000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[15370.472000]  sdb: [mac] sdb1 sdb2 sdb3 sdb4
[15370.480000] sd 5:0:0:0: [COLOR="Red"][sdb][/COLOR] Attached SCSI disk
[15370.480000] sd 5:0:0:0: Attached scsi generic sg2 type 0

```

In this case, the device attached as **/dev/sdb**. 

2. While Ubuntu is booting, try hitting Cntl-F1 to see if there are any messages that might explain the problem.

why while it is booting? (Thanks for answering:))

---

### Post by jerome1232 on 2008-12-19
> **inxygnuu said:**
> why while it is booting? (Thanks for answering:))

Because it will give you detailed text messages about exactly what is going on while the machine is booting up, and may give a hint as to what's going on.

---

### Post by inxygnuu on 2008-12-20
> **jerome1232 said:**
> Because it will give you detailed text messages about exactly what is going on while the machine is booting up, and may give a hint as to what's going on.

Thanks!

---

