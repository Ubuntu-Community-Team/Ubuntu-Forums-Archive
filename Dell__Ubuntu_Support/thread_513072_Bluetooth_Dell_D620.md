---
title: "Bluetooth Dell D620"
date: 2007-07-30
forum: Dell  Ubuntu Support
---

### Post by aitorcalero on 2007-07-30
Does anyone can configure successfully bluetooth on Dell LATITUDE D620?
I have installed all bluetooth required packages, but I cannot make it work. When I run hciconfig (scan) it shows the following message:
```
Can't get device info: No such device
```
How do I know if there is any bluetooth present in my laptop?
Any help will be much appreciated.

---

### Post by anubhavrocks on 2007-07-30
can you try this command and post the output

```
sudo lsusb -v|grep -i bluetooth
```

---

### Post by Borealis on 2007-08-16
> **anubhavrocks said:**
> can you try this command and post the output

```
sudo lsusb -v|grep -i bluetooth
```

Hi, I've got the exact same laptop and cant get bluetooth working. This is the output:
discodave@discodave-laptop:~$ sudo lsusb -v|grep -i bluetooth
Bus 005 Device 004: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
  bDeviceProtocol         1 Bluetooth
  idProduct          0x8103 Wireless 350 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth


any help would be appreciated

---

### Post by sebasapri on 2007-09-02
Hi, I've got the exact same laptop and cant get bluetooth working.
Anybody can make work this infernal bluetooth.
please reply ...
greetings.

:popcorn:

i find this:

[http://forums.techarena.in/showthread.php?t=588829](http://forums.techarena.in/showthread.php?t=588829)  , probe this and coment if  anybody worked.

---

