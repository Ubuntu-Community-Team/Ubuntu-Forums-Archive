---
title: "wireless drivers help"
date: 2007-05-07
forum: Desktop Environments
---

### Post by trevelyn on 2007-05-07
hi, i started using ubuntu because of the package manager.  apt-get.  I am fro a Slackware background and always hated searching for dependencies that needed dependencies...inf!
I really like it her in the Ubuntu, and i feel ubuntu. I installed it on 5 of my servers here in the lab, and have a driver issue.  I have usb wireless cards from linksys that work great with ubuntu on my laptop (macbook newest rev) under the serialmonkey drivers naming it "rausb0."  The old version 6.0x of ubuntu didn't even find the card and installing the serialmonkey drivers wasn't an issue, very easy.  but feisty 7.04 found the card under false pretenses.  and named it wlan0 which i have only seen with prism chipset based cards, mine is ralink=rausb0.  i downloaded the drivers like i normally do, and installed them, and ran "modprobe rt73"  put in the card and it was still "wlan0"  )the name means nothing really except that the drivers associated with the name wont let me change modes/add keys/change nicknames/change extended service set id/etc..) then i troed to remove the prism drivers by  "modprobe -l | grep prism" then "modprobe -r <every prism driver module here> then unplugged the usb device ran modprobe rt73 again, and STILL! wlan0 :/
now i don;t understand.. like modprobe was ignoring me?? so i followed the paths to the kernel modules and deleted ALL of the prism modules, reboot, ran modprobe rt73 plugged in the device and still.. wlan0 and crappy drivers.  i am so confused right now, any ideas??

---

### Post by trevelyn on 2007-05-11
okay i found out myself, if i install Ubuntu with the card plugged in it finds the drivers for it and installs the wrong drivers, i just have to plug it in and install it after the Full install of the OS. :)

---

