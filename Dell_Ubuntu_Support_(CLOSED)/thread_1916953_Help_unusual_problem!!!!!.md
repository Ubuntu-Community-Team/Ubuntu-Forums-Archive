---
title: "Help unusual problem!!!!!"
date: 2012-01-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by divyanshu308 on 2012-01-29
Hi everyone I've got a very bad situation.
I have a Dell inspiron 15r.
It had dual boot windows7 and Ubuntu.
I wanted to make a fresh install of both windows and Ubuntu.
When i booted win 7 DVD i accidentally deleted the Ubuntu swap partition.
Now the laptop doesn't turns on.
it's stuck at the boot screen.
I even removed the hard disk and tried to connect it to my desktop using sata to USB converter but it's not being detected it's spinning even showing an icon as if there is a USB device connected but no partitions showing.
I live booted Ubuntu without the hare disk plugged in and it works fine but obviously since no hard disk is connected there is no place to install.
Even when it's live booted up when i connected the hard disk nothing shows up.
Please help....

---

### Post by Elfy on 2012-01-29
Boot the livecd - use the Try option. Once it's booted follow this and paste the result here for us

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by divyanshu308 on 2012-01-29
this is what happened in terminal.

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script.sh

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
no block devices found

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Desktop/".

ubuntu@ubuntu:~$ 


this is the results.txt file contents

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================


============================ Drive/Partition Info: =============================

no valid partition table found
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========= Devices which don't seem to have a corresponding hard drive: =========

no block devices found 




right now while in live boot i have my harddisk removed beacuse it does not let me boot up the laptop.

---

### Post by divyanshu308 on 2012-01-29
after posting the message i connected the hardisk (i'm still in the live boot mode) but it doesnt shows any disk connected...

i'll re run the same script again after this and post the result...

---

### Post by divyanshu308 on 2012-01-29
ran the script again with disk connected.
here is the terminal output.


ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script.sh

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.


Identifying MBRs...
Computing Partition Table of /dev/sda...


thats it there is no progress after this...

---

### Post by divyanshu308 on 2012-01-29
just out of curiosity i ran gparted and its detecting the hard disk.
but there are no partitions.!!
i'm showing the image..

---

### Post by divyanshu308 on 2012-01-30
Some body please help..

---

### Post by YannBuntu on 2012-01-30
Hello
Connect your disk.
if you want to recover documents, try TestDisk.
Then reinstall Windows, then Ubuntu.

---

### Post by divyanshu308 on 2012-01-31
> **YannBuntu said:**
> Hello
Connect your disk.
if you want to recover documents, try TestDisk.
Then reinstall Windows, then Ubuntu.

Thanks So much Buddy You saved my day
I love you
Right now I have installed Windows 7 Still the rest of partitions are not visible.
But still buddy thanks you sooooo much..

---

### Post by raja.genupula on 2012-01-31
> Right now I have installed Windows 7 Still the rest of partitions are not visible.
if you install windows 7 then your Grub loader will be overwrite . you need to reinstall grub loader to get your Ubuntu . 

look at my signature for grub recovery . 
All the best.

---

