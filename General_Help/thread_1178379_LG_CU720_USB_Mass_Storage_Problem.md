---
title: "LG CU720 USB Mass Storage Problem"
date: 2009-06-04
forum: General Help
---

### Post by XVII on 2009-06-04
I am currently running:

OS:  Ubuntu 9.04
KERNAL:  2.6.28-11-generic
DE:  GNOME 2.26.1

When I connect my LG SHINE (CU720) to my computer via USB mass storage nothing shows up in "/proc/bus/usb" and the computer does not react at all.  The phone, however, lights up and proceeds to charge itself and says that it is connected via USB mass storage.

I have tried to connect using the phone's music sync setting but this yielded the same result.  I did however have minor success when I attempted to connect with the data service setting.  The computer brought up a dialog and recognized the phone for data service, but this is not what I need.

Any help would be appreciated very much.

---

### Post by Chronon on 2009-06-04
UMS functionality is a bit broken for certain devices recently due to libgphoto and libmtp bugs.  They incorrectly identify MSC devices as MTP and prevent mounting as a UMS device.  I have two different DAPs that connect via MSC and neither of them show up consistently because of this problem.  It's supposedly fixed upstream.

[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998)

---

### Post by XVII on 2009-06-04
Thanks for the quick reply.  Hopefully this will be corrected soon.

---

### Post by dowcet on 2010-06-08
I have the same exact problem described in the initial posting, still in Ubuntu 10.04, and am looking for a solution. 

[A bug report]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/477031") regarding another LG phone suggests a workaround. 

> Comment out in /lib/udev/rules.d/61-option-modem-modeswitch.rules  this line:
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="1000",  RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t  option-zerocd"
Then it works with option_zero_cd=2, eject and one minute reconnect,  just as in 9.04.


I guess "option_zero_cd=2" is a line to add to the file /etc/modules. When I did these two things, I was able to connect my LG CU720 one time in mass storage, which was good... but when I started copying files onto the phone, it froze after about 200 megabytes transfered, and wouldn't re-connect to my computer. So, I'm still looking for a real solution  :confused:

---

