---
title: "DELL Inspiron 700m Wireless not working in Ubuntu 7.04"
date: 2007-08-24
forum: Dell  Ubuntu Support
---

### Post by ubume on 2007-08-24
Hi,

I have a Dell Inspiron 700m and just installed Ubuntu 7.04 (Fiesty Fawn) a few days ago.  Everything went smoothly except for the wireless network.  I am able to confure the wireless network and set the SSID and WEP password.  However, it does not recognize my wireless access point.  I have been googling for how to and tips and did not found exactly a step by step recipe that works.  If any one can help, it is very much appreciated.

---

### Post by moore.bryan on 2007-08-24
[I]what are the outputs of ```
lspci
iwconfig
```?
the first will tell us about your pci stuff and the second wireless stuff.
[/I]

---

### Post by ruddy on 2007-08-25
Check this thread to see if it works for you. It did for my Latitude D600.

[http://ubuntuforums.org/showthread.php?t=405990]("http://ubuntuforums.org/showthread.php?t=405990")

---

### Post by ubume on 2007-08-29
Thanks to all who responded.  I finally got it to work.  I installed the NDISWrapper tool and use the NDIS driver from WinXP.  That worked!.

---

### Post by shuttleworthwannabe on 2007-08-29
ubume, could you please share with us how you installed the ndiswarpper and got the card to work; I have the same dell 700m on my wife's machine and am planning to install feisty on it. A step by step would really help.

S

---

### Post by err on 2007-09-04
I also have 700m and have installed Ubuntu 2 days ago... first time ever:) 

Spent about 15 minutes googling how to install the Dell WLAN card that I have and stumbled upon this website:

[http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated](http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated)

Followed it, reboot and bingo... WLAN is working. 

The only other thing I need to do on my 700m is to get the Intel 855 resolution video to support 1280x800. 

Now everything works perfect. Much better system performace on Ubuntu vs Vista on this 700m:)

---

### Post by moore.bryan on 2007-09-04
> **err said:**
> The only other thing I need to do on my 700m is to get the Intel 855 resolution video to support 1280x800. 
*the 915resolution package **might** fix that problem...*

---

### Post by shuttleworthwannabe on 2007-09-07
ditto to that get it from synaptic (915resolution). It can be a mission getting the res right of you do not know about this trick

---

