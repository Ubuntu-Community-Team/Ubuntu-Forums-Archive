---
title: "Yes, another Broadcome issue (2.6.17) - I swear its not superfluous"
date: 2006-06-21
forum: Desktop Environments
---

### Post by underdog on 2006-06-21
I was so excited when I heard 2.6.17 came with native broadcom support, so i spent about 2 hours configuring and compiling the new kernel. Now, it still doesn't work. I have a Compaq Presario v5102NR. It has the Broadcom chipset. I have a wireless button (not on the keyboard) that lights up in windows when active. After install 2.6.17, rebooting, blah blah, in my network settings I have eth0 as my ethernet card, eth1 (not wlan0?) as my wireless card (it says it is a wireless connection). I can activate it, but it doesn't show up in network tools, and it doesn't work. Any ideas? I've looked around, but no one seems to have run into this yet.

---

### Post by PWill on 2006-06-21
which broadcom model do you have? also, have you tried using bcm43xx-fwcutter?
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by underdog on 2006-06-21
Now it is kind of working...I installed the bcm43xx-fwcutter, and my wireless light now comes on, but I'm having another problem (4318 btw)


```

underdog@underdog-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device eth1 has been compiled with version 20
of Wireless Extension, while this program supports up to version 19.
Some things may be broken...

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

underdog@underdog-laptop:~$ sudo iwlist eth1 scan
Password:
Warning: Driver for device eth1 has been compiled with version 20
of Wireless Extension, while this program supports up to version 19.
Some things may be broken...

eth1      No scan results
```

---

### Post by mshirey8 on 2006-06-22
I have a presario v2000 with broadcom. I used ndiswrapper to install the drivers that came with the machine. It identiies my wireless as eth1 and the button only lights up when there is activity - not all the time like in windoze or Breezy. Note: I do not have network manager installed since it appears to create a conflict.

---

