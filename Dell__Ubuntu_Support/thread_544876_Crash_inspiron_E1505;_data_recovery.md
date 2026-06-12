---
title: "Crash inspiron E1505; data recovery?"
date: 2007-09-06
forum: Dell  Ubuntu Support
---

### Post by honeycomb on 2007-09-06
How can I save my data on a USB stick before I have to reinstall Ubuntu  on my Inspiron E1505?

Which commands mount the stick?
How do I set the file system on the stick?
How do I list the directory on the stick?

I get the message X server cannot start in 60 seconds.

Thanks,
honeycomb

---

### Post by honeycomb on 2007-09-07
Some details:
root@dell:~# lsusb
Bus 005 Device 002: ID 08eC:0016 M-Systems Flash Disk Pioneers
root@dell:~# df
...
procbususb  513228  116  513112  1%   /proc/bus/usb
...

root@dell:~# lsmod
...
usbcore 134280  6  hsfosspec,usb_storage,libusual,ehci_hcd,uhci_hcd
...
root@dell:~# cat /etc/fstab
# /dev/sda1  ... ext3
# /dev/sda5  ... swap
# /dev/scd0  ...  udf,iso9660  ...  /media/cdrom0
root@dell:~# ls -l /media
l ... root  root   6 ...  cdrom -> cdrom0
d ...root  root 1024 ... cdrom0
d ... root root      0  ...  usbdrive
root@dell:~#

Which commands are missing so I could see the data on the USB stick?
Thanks, honeycomb

---

### Post by honeycomb on 2007-09-07
Hi
I am mounted but still no listing of files on the USB stick?
mount -t usbfs /dev/sdb /media/usb
ls -l /media/usb
d ...    6    001
d ...    6    002
d ...    6    003
d ...    6    004
d ...    6    005
   ...    6    devices
ls -l /media/usb/005
d ...    6   001
d ...    6   003
ls -l /media/usb/005/003
 ...   root root 50  ... /media/usb/005/003

What does this mean? No listing of files?
Do I have wrong file system definition?
Thanks, honeycomb.

---

### Post by bimbo on 2007-09-07
You'll want to read about pmount, I'd say.

Using 
pmount sdX 
will put sdX to /media/sdX

---

### Post by neptho on 2007-09-07
Have you tried just resetting your X configuration?

Login to the terminal with your username and password, then reconfigure your X server.

```
%sudo dpkg-reconfigure xserver-xorg
```

---

### Post by honeycomb on 2007-09-08
Hi
I tried to reset/repair the X server as you proposed but it did not repair the booting into graphics screen.

I tried to initialize graphics by booting in "recovery mode" ( press esc after DELL Boot screen)  that will invoke 4 possible boot options.

Then when asked, type root (admin) password.

Then type a line command:  sudo init 5 
That will restart graphics login screen, you can login as user and plug in USB stick, and backup data.

Then there was no way how to restore proper boot up into graphics screen.  I downloaded all packages available. I had to reinstall Ubuntu by choosing the last option in the boot menue that deletes all data and restores Ubuntu like at the time of fab delivery.

Then I did the update with 160 packages.
And now everthing works fine. I restored all user data and have faith in future adventures.

Thanks, honeycomb.

---

