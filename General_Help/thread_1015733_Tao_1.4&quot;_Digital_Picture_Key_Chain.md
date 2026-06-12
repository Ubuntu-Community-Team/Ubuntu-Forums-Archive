---
title: "Tao 1.4&quot; Digital Picture Key Chain"
date: 2008-12-19
forum: General Help
---

### Post by Voorhees1979 on 2008-12-19
Hi there

I bought one of these Tao 1.4" digital key chains just to see what they were like. I am having problems getting Ubuntu to mount it. I was hoping it would auto mount as a storage device like my other stuff.

When i type lsusb i get:

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 093a:020f Pixart Imaging, Inc.
Bus 001 Device 003: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 001 Device 001: ID 0000:0000
 Its being picked up as Pixart Imaging but not mounting

Any help would be great.

[www.taoelectronics.com](www.taoelectronics.com) is there website

Many Thanks

---

### Post by blazemore on 2008-12-19
Can you post the output of ```
fdisk -l
```

---

### Post by Voorhees1979 on 2008-12-19
Hi

Thanks for the reply the output is:

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00011c72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4866    39086113+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a0ea5d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0baa0ca5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        3579    28748286   83  Linux
/dev/sdd2            3580        3738     1277167+   5  Extended
/dev/sdd5            3580        3738     1277136   82  Linux swap / Solaris

---

### Post by blazemore on 2008-12-19
The device isn't showing as storage. (Unless it's 40gb lol) so beyond that I can't help you.

Unless...
well you DID do fdisk -l with the device plugged IN, right?

---

### Post by Voorhees1979 on 2008-12-19
hehe no its not 40g, more like a few meg i would think. Its only a cheap one. Yes it is plugged in. I guess it needs a driver then :(

Thanks for your help. Might have to find a spare hd and install windows. Seems a bit of a nightmare just for this little key chain though.

---

### Post by blazemore on 2008-12-19
That is quite annoying.

One more time. Unplug it, plug it in again, and run
```
sudo fdisk -l
```

And tell us again

Oh, and put it in [code ] tags plz

---

### Post by Voorhees1979 on 2008-12-19
```
voorhees@voorhees:~$ sudo fdisk -l
[sudo] password for voorhees: 

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00011c72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4866    39086113+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a0ea5d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0baa0ca5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        3579    28748286   83  Linux
/dev/sdd2            3580        3738     1277167+   5  Extended
/dev/sdd5            3580        3738     1277136   82  Linux swap / Solaris
voorhees@voorhees:~$ 


```

Doesnt look like it wants to show up

```
voorhees@voorhees:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 093a:020f Pixart Imaging, Inc. 
Bus 001 Device 003: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 001 Device 001: ID 0000:0000  
voorhees@voorhees:~$ 

```

Its still showing there so it is being detected that its plugged in.

---

