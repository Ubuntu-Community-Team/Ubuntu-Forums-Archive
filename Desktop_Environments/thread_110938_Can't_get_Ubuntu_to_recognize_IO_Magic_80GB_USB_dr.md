---
title: "Can't get Ubuntu to recognize I/O Magic 80GB USB drive"
date: 2006-01-01
forum: Desktop Environments
---

### Post by Classic_gamer on 2006-01-01
I have an I/O Magic 80GB Gigabank USB drive that's formated as fat32 and Ubuntu 5.10. I plug it in and it doesn't show up anywhere. I've tried mounting by doing:

mount -t vfat /dev/hdb/ /mnt/TempHD/
(I created a TempHD folder in /mnt/)
and when that didn't work (I didn't think it would), it tried
mount -t vfat /dev/sda/ /mnt/TempHD/

I'm basicly a Linux newb, so go easy.

EDIT: I realized that I had -f instead of -t

---

### Post by Classic_gamer on 2006-01-01
OK. Well now it won't recognize any of my USB drives. Even the ones that I know worked before.

---

### Post by kaamos on 2006-01-01
Is gnome-volume-manager running?

---

### Post by Classic_gamer on 2006-01-01
gnome-volume-manager is running. Now, for some reason, my other USB drives have decied to work again, but this one still isn't. When I plug it in and do an lsusb, lsusb hangs and doesn't do anything.

---

### Post by kaamos on 2006-01-01
Try mounting manually with
```
sudo mount /dev/sda**X** /mnt/TempHD
```
where X is 1 or 2 or 3.. depending on your amount of usb-drives. Does it give an error or does the drive mount?

---

### Post by Classic_gamer on 2006-01-01
I only have this USB drive pluged in, so I did a ```
sudo mount /dev/sda1 /mnt/TempHD
```
but it tells me I need to specify the filesystem type, so I do a
```
sudo mount -t vfat /dev/sda1 /mnt/TempHD
```
and it tells me that /dev/sda1 doesn't exist.

---

### Post by kaamos on 2006-01-01
When you plug the drive in then use commad "dmesg | tail -n 25", what is the output?

---

### Post by Classic_gamer on 2006-01-01
Well. Here's the output for ya: ```
[4295014.982000]  [<f8df527b>] storage_disconnect+0x50/0x6a [usb_storage]
[4295014.982000]  [<f891b09c>] usb_unbind_interface+0x36/0x65 [usbcore]
[4295014.982000]  [<c01ec138>] device_release_driver+0x49/0x55
[4295014.982000]  [<c01ec2f1>] bus_remove_device+0x48/0x77
[4295014.982000]  [<c01eb6dc>] device_del+0x43/0x6f
[4295014.982000]  [<f89209cb>] usb_disable_device+0x77/0xe9 [usbcore]
[4295014.982000]  [<f891cb77>] usb_disconnect+0x93/0xec [usbcore]
[4295014.982000]  [<f891d7c6>] hub_port_connect_change+0x57/0x2b2 [usbcore]
[4295014.982000]  [<f891dc43>] hub_events+0x222/0x2c6 [usbcore]
[4295014.982000]  [<f891dce7>] hub_thread+0x0/0xe8 [usbcore]
[4295014.982000]  [<f891dd03>] hub_thread+0x1c/0xe8 [usbcore]
[4295014.982000]  [<c012469a>] autoremove_wake_function+0x0/0x3a
[4295014.982000]  [<f891dce7>] hub_thread+0x0/0xe8 [usbcore]
[4295014.982000]  [<c012469a>] autoremove_wake_function+0x0/0x3a
[4295014.982000]  [<c0101245>] kernel_thread_helper+0x5/0xb
[4295014.982000] Code: 89 02 74 03 89 50 04 c7 41 04 00 02 20 00 89 5c 24 10 8b 46 08 89 44 24 0c 5b 5e e9 6b a4 fe ff 5b 5e c3 55 57 56 53 8b 44 24 14 <8b> 58 48 8b 50 08 ff 4a 70 0f 88 b9 00 00 00 8b 53 0c 8d 6a fc
[4295014.982000]  <6>agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4295075.967000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4295075.967000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
[4295383.311000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4295383.311000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4295383.311000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
[4295481.455000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4295481.455000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4295481.455000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
 
``` Now. Those little messages about USB drives and stuff could be from me plugging and unplugging my other USB drive.

---

### Post by kaamos on 2006-01-01
Ok, this is total speculation but try with a different usb-port and give the output again. This could help to locate the problem.

---

### Post by Classic_gamer on 2006-01-01
OK. I plugged it into one of the USB ports on the back of my computer and here's the output: ```
[4295014.982000]  [<f8df527b>] storage_disconnect+0x50/0x6a [usb_storage]
[4295014.982000]  [<f891b09c>] usb_unbind_interface+0x36/0x65 [usbcore]
[4295014.982000]  [<c01ec138>] device_release_driver+0x49/0x55
[4295014.982000]  [<c01ec2f1>] bus_remove_device+0x48/0x77
[4295014.982000]  [<c01eb6dc>] device_del+0x43/0x6f
[4295014.982000]  [<f89209cb>] usb_disable_device+0x77/0xe9 [usbcore]
[4295014.982000]  [<f891cb77>] usb_disconnect+0x93/0xec [usbcore]
[4295014.982000]  [<f891d7c6>] hub_port_connect_change+0x57/0x2b2 [usbcore]
[4295014.982000]  [<f891dc43>] hub_events+0x222/0x2c6 [usbcore]
[4295014.982000]  [<f891dce7>] hub_thread+0x0/0xe8 [usbcore]
[4295014.982000]  [<f891dd03>] hub_thread+0x1c/0xe8 [usbcore]
[4295014.982000]  [<c012469a>] autoremove_wake_function+0x0/0x3a
[4295014.982000]  [<f891dce7>] hub_thread+0x0/0xe8 [usbcore]
[4295014.982000]  [<c012469a>] autoremove_wake_function+0x0/0x3a
[4295014.982000]  [<c0101245>] kernel_thread_helper+0x5/0xb
[4295014.982000] Code: 89 02 74 03 89 50 04 c7 41 04 00 02 20 00 89 5c 24 10 8b 46 08 89 44 24 0c 5b 5e e9 6b a4 fe ff 5b 5e c3 55 57 56 53 8b 44 24 14 <8b> 58 48 8b 50 08 ff 4a 70 0f 88 b9 00 00 00 8b 53 0c 8d 6a fc
[4295014.982000]  <6>agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4295075.967000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4295075.967000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
[4295383.311000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4295383.311000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4295383.311000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
[4295481.455000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4295481.455000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4295481.455000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode

``` EDIT: Oh yeah, also, I heard a clicking noise comming from the drive after I plugged it in, so I unplugged it.

---

### Post by Classic_gamer on 2006-01-01
Stupid computer. Sorry for the double post

---

### Post by Classic_gamer on 2006-01-01
Stupid computer. Sorry for the double post

---

