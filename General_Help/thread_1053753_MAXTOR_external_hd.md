---
title: "MAXTOR external hd"
date: 2009-01-29
forum: General Help
---

### Post by robbiehoodyso on 2009-01-29
hello,



im having trouble seeing my maxtor external hard drive.

when i lsusb

Bus 004 Device 004: ID 0d49:3210 Maxtor 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 0000:0000  

it shows up but i cannot see it on my desktop or anywhere else.
i have  all the ntfs config files and did everything that it said in thread 523245.

thanks for any help, 


robbie

---

### Post by jms1989 on 2009-01-29
Post the output of df -h. If you can see it as /dev/sda1, then try mounting it. Use (sudo mount -t vfat /dev/sda1 /media/usbdev) to mount it. Replace sda1 with the actual device and replace usbdev with a folder of your choice. If that folder doesn't exist, create it with sudo mkdir /media/newfolder.

---

