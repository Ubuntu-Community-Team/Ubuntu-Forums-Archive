---
title: "Battery state problem on laptop"
date: 2009-02-22
forum: General Help
---

### Post by Guus1982 on 2009-02-22
Ive downloaded the live cd file and installed it on my laptop as in dual boot (toshiba satelite 100/a). So far so good (besides a lot of locationerrors at starting up). After that i wanted to instal ubuntu on my laptop HP nc4400 and there it went bad. I was also trying to create a dual boot but when ubuntu tried to create a partition the setup crashed and on rebooting i recieved the information that my partition was damaged. After restoring the harddrive which was erased completely i tried to install ubuntu again. 
 
 For the record this laptop does not have an cd drive, so i created an bootable usb stick with the ubuntu install on the other laptop.
 
 But now im stuck: every time i boot from the usb stick it shows the progression bar and then gives me this message:
 
 "setupcon: None of /etc/default/console-setup nor /.console-setup exists
 Checking Battery State OK"
 
 and then nothing happens..

---

### Post by Guus1982 on 2009-02-22
please can someone guide me in the right direction i really want my laptop back and running...

---

### Post by Guus1982 on 2009-02-23
i figured it out

made another bootable usb stick with fdisk

made a partition on the drive (there were no partitions)

then formated this partition and voila ubuntu was installed without any problems

it works it works

---

