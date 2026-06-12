---
title: "Dell Studio - bluetooth not found"
date: 2008-11-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kewsvnet on 2008-11-04
Using Ubuntu on my Dell Studio 1535 i recently discovered that turning bluetooth off in Windows Vista, causes Ubuntu not to see the Bluetooth device at all. Took me a while to figure out the problem, just thought it might be useful to anyone else having a similar problem

---

### Post by superm1 on 2008-11-04
You should be able to turn it back on by running these commands generally:

```
sudo hid2hci --tohci
sudo dellWirelessCtl --sw_bt 1 --bt 1
```

---

### Post by tckb on 2008-11-12
mine is the same problem do i need to do that every time... whats the problem??????

---

### Post by sean0105 on 2009-08-08
not working.... it said "No devices in HID mode found"
so how to solve this matter? pls help

---

### Post by Aki0550 on 2009-12-10
Hello there
I have same problem, and my bluetooth is off and can't turn it on. I've seen comands i have to put but have question where i should write these commands so my bluetooth is turned on.
Thanks

---

### Post by teward on 2009-12-11
Plz do me this favor:

Run commands;

lspci
lsusb


Print outputs for me to see.  To check and see if you even have bluetooth.

FYI: I'm high on coffee... explains the bad english... zZzZZzZz...

---

