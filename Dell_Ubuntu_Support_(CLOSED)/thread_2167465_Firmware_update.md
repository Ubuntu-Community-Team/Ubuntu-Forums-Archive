---
title: "Firmware update"
date: 2013-08-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by CampSoup1988 on 2013-08-13
I am trying to update some of my Dell Dimension 5150's firmware, but I am not quite sure how to do this.  I am running Ubuntu 13.04 64-bit on the computer without Windows.

The best explanation that I could find is these two documents, but it seems that they were last updated in 2007, so I don't know if they are too old now.

[http://linux.dell.com/wiki/index.php/Firmware-tools_announcement](http://linux.dell.com/wiki/index.php/Firmware-tools_announcement)

[http://linux.dell.com/wiki/index.php/Oss/Firmware_Tools/Admin_Guide](http://linux.dell.com/wiki/index.php/Oss/Firmware_Tools/Admin_Guide)

Thank you in advance.

---

### Post by tripp98 on 2013-08-15
please check out the following

[http://giantdorks.org/alain/how-to-update-dell-bios-firmware-regardless-of-the-os-linux-unix-whatever/](http://giantdorks.org/alain/how-to-update-dell-bios-firmware-regardless-of-the-os-linux-unix-whatever/)

in short
install unetbootin
create freedos boot usb
copy bios file .exe to usb
boot freedos then from a:
type c:
then type name of bios update file.
should flash up.
used it many times.

---

### Post by CampSoup1988 on 2013-08-15
> **tripp98 said:**
> please check out the following

[http://giantdorks.org/alain/how-to-update-dell-bios-firmware-regardless-of-the-os-linux-unix-whatever/](http://giantdorks.org/alain/how-to-update-dell-bios-firmware-regardless-of-the-os-linux-unix-whatever/)

in short
install unetbootin
create freedos boot usb
copy bios file .exe to usb
boot freedos then from a:
type c:
then type name of bios update file.
should flash up.
used it many times.

I was reading those instructions for the bios, but I did not know about firmware updates

---

### Post by tripp98 on 2013-08-15
i have just used the freedos usb and the file from dell.  the other part is if you try to run it in ubuntu.  never had one run in ubuntu.

---

### Post by CampSoup1988 on 2013-08-15
> **tripp98 said:**
> i have just used the freedos usb and the file from dell.  the other part is if you try to run it in ubuntu.  never had one run in ubuntu.

In other words, the firmware updates are done the same way as the bios updates?

---

### Post by tripp98 on 2013-08-15
appears so.  i have used it on many different workstations.  precision/optiplex
are you just trying to update the bios? 
or do you have raid controllers to update?
i just used the freedos method for the bios.

---

### Post by CampSoup1988 on 2013-08-15
Initially I saw on Dell's site, they have firmware updates for some of the motherboard's chipsets and such.   I don't think driver updates (from Dell's website) apply since I am using Ubuntu instead of Windows.  Correct?

Firmware updates:
[LIST]
[*][HLDS GCC4482B HH 48X CDRW/DVDROM Firmware Update]("http://www.dell.com/support/drivers/us/en/555/DriverDetails/Product/dimension-5150x?driverId=MKD83&osCode=WLH&fileId=2731096915&languageCode=en&categoryId=RS") 
[/LIST]

PS: Looking over the list, I did not realize the rest of the updates were either applications (I wish I could run Dell's web application that scans your computer's hardware and update their records of what is in the computer).  I also found that there is indeed like 5 BIOS updats.

---

### Post by tripp98 on 2013-08-15
havent flashed a dvd drive in years.  many years ago there was the odds of turning them to rocks if it didnt go perfect.  unless you are having issues dont update the dvd drive.  also notice that the update is from 2007.  if its worked this long then you are probably ok.  if the drive "quits working" then you have nothing to loose.

most of the updates are windows drivers updates as you said.  really the only thing to flash up is the bios or raid cards.

---

### Post by CampSoup1988 on 2013-08-15
Ok, thank you.  The manufacture date of this computer is 12/13/2005.  I aquired it from in front of someone's house. (I knocked at verified that they were giving it away.  I was quite impressed that this computer has a [3.0 GHz 64-bit Pentium 4 processor]("http://ark.intel.com/products/27478/Intel-Pentium-4-Processor-630-supporting-HT-Technology-2M-Cache-3_00-GHz-800-MHz-FSB")!  All I had needed to do was upgrade the ram (it only had 512 MB of ram) and install a hard drive (did not come with one))

---

### Post by ubu2008 on 2013-08-20
I tried Trip98's suggestion, and it did not work for me. The following worked for me. Caution: I used windows for part of the process.
I did it on 2013/06/18.

TO UPDATE BIOS this method worked (on 14z) but probably works everywhere. Other methods did not work.

Machine:
Do all this on Window machine.

Ingredients:
simple window os   win98boot
hp utility to make bootable disk    hpflash:
the microcode file (for 14z last time)  BMWZrA12.exe

Process:
install hpflash
using hpflash, create bootable disk using win98boot
cp to the same USB, the payload BMWZ4A.exe

Go to the target machine:
shutdown, insert usb, bootup into win98boot
in win98, start dos window
in dos window, execute BMWZ4A12.exe
Note that using other methods to create bootable windows did not work.

---

