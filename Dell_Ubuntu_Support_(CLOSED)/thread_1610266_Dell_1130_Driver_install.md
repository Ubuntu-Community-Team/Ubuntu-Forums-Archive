---
title: "Dell 1130 Driver install"
date: 2010-10-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kevin Jones on 2010-10-31
Hello all,
I have a fresh install of 10.10
I also have a Dell 1130 lazer  printer. I cannot get them to work together.
I went to Dell driver support and downloaded the following:

Printers: Dell 1130,v.1.07_LINUX,AOO

[Linux:[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&SystemID=PRN_1130&servicetag=5HSSYK1&os=LNUX&osl=en&catid=-1&impid=-1&dateid=-1&typeid=-1&formatid=-1&source=&fileid=393786]](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&SystemID=PRN_1130&servicetag=5HSSYK1&os=LNUX&osl=en&catid=-1&impid=-1&dateid=-1&typeid=-1&formatid=-1&source=&fileid=393786])


There is an option for ubuntu 8.04 which I did not take since it seems to be the same driver.
The download arrived as a tar: Dell1130_Linux_1.07.tar.gz
I think this is where I started to go wrong.
Untar produced a file called cdroot inside 'cdroot' are two files. Autorun and Linux.

from this point can anyone help me to install the driver, I do not know what file to go to in order to run dpkg or gdebi

thanks very much

Kevin

---

### Post by mikewhatever on 2010-11-01
You need to run the autorun file.

cd cdroot

sudo ./autorun

---

### Post by Kevin Jones on 2010-11-01
Mike,
It worked like a charm!!

I owe you one.
Thanks
Kevin

---

### Post by mikewhatever on 2010-11-02
Welcome.O:)

---

