---
title: "USB TV Stick"
date: 2006-09-15
forum: Desktop Environments
---

### Post by rarstar on 2006-09-15
Any ideas if something like this will work under Ubuntu?

[http://www.aria.co.uk/ProductInfoComm.asp?ID=20886&SpecialStatus=1](http://www.aria.co.uk/ProductInfoComm.asp?ID=20886&SpecialStatus=1)

Thanks,
rar

---

### Post by anaconda on 2006-09-15
Some of them can be made to work in ubuntu..

The problem is that MSI sells 2 different chipsets with the same product name "mega sky 580", and only one of them can easily be made to work with ubuntu.. 

it can be checked by plugging the stick in the machine and typing "sudo lsusb -v" and searching the part: iManufacturer..
DTV USB MINI sticks are supported, but PC-DTV RECEIVER ones are not!

here are few links that might be of interest:
[http://permalink.gmane.org/gmane.linux.drivers.dvb/27082](http://permalink.gmane.org/gmane.linux.drivers.dvb/27082)
[http://www.rasterburn.org/~aet/msi/](http://www.rasterburn.org/~aet/msi/)
[http://forum.ubuntu-fi.org/index.php?PHPSESSID=0547e35fdf2a9e52c5035815b7cd9e87&topic=3038.msg21104](http://forum.ubuntu-fi.org/index.php?PHPSESSID=0547e35fdf2a9e52c5035815b7cd9e87&topic=3038.msg21104)

I might be buing the exact same stick.. but maybe it would be easier to buy one that kernel supports without any tweaks..

---

