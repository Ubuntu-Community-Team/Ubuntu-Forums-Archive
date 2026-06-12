---
title: "ubuntu 12.04 64bit - problem with usb3 port"
date: 2012-06-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by madvinegar on 2012-06-04
Hi all. I have a dell inspiron n411z laptop.
It has 2 usb3 ports and one usb2 port.

I have installed ubuntu 12.04.

I am getting internet through a huawei e173 dongle of O2. (I don't know if this is relevant).

While the dongle is recognized by both ports (the light comes up and I get results from lsusb), it only works and comes up in network manager in the usb2 port.
It is not a problem of the dongle because in windows7 it works in all ports. (so probably is not a Dell matter either).

I have read in google that there is somekind of problem with the usb3 ports in ubuntu 12.04. It affects also external usb hard drives etc.

For your reference I will state below the lsusb results of the dongle when plugged in usb2 and when plugged in usb3.

In USB3:
```
Bus 003 Device 003: ID 12d1:1446 Huawei Technologies Co., Ltd. E1552/E1800 (HSPA modem)
```

In USB2:
```
Bus 002 Device 005: ID 12d1:1436 Huawei Technologies Co., Ltd.
```

As you see, it has a different ID and a different description which is very very odd. Is this somekind of bug? 
Any help or advise will be greatly appreciated.

---

### Post by madvinegar on 2012-06-05
I managed to solve the problem as follows:

I have gone through terminal to: 
```
gksudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules
```

and changed the line
```
# Huawei E173
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1557", RUN+="usb_modeswitch '%b/%k'"
```

to
```
# Huawei E173
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1436", RUN+="usb_modeswitch '%b/%k'"
```


i.e. I changed the "1557" to "1436" as I knew that theID that worked when it was plugged in the usb2 port was "12d1:1436".

I saved the file, exited and then plugged the huawei stick and it was recognized and worked immediatelly.

The lsusb result after that became:
```
Bus 003 Device 004: ID 12d1:1436 Huawei Technologies Co., Ltd.
```


Ofcourse I cannot explain why it was recognised just fine in the usb2 port by default, while in the usb3 port I had to do the above changes...

---

### Post by harrygc on 2013-01-08
Thanks madvinegar! That was very useful. I recently bought ThinkPad X1 and noticed that my old USB 3G dongle stopped working. Your post helped me find the issue and it fixed it! To fix in my case I ran 'lsusb' which had line:

Bus 003 Device 002: ID 12d1:1446 Huawei Technologies Co., Ltd. E1552/E1800 (HSPA modem)

So I added this new line to the file, just below other E173 specs

# Huawei E173
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1446", RUN+="usb_modeswitch '%b/%k'"

It worked!

---

