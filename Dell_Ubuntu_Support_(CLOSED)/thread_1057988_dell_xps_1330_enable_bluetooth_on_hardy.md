---
title: "dell xps 1330 enable bluetooth on hardy"
date: 2009-02-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by manix user on 2009-02-02
My bluetooth applet on ubuntu 8.04 can't detect the bluetooth device. I've read some posts that say I need to log into Vista( I have a dual boot ), enable it from there and then log into ubuntu. 

Is there any tool I can use to control my bluetooth device from ubuntu ?

---

### Post by superm1 on 2009-02-02
Some (although seemingly not many) people do have some successes with using the "hid2hci" tool combined with enabling it with libsmbios (dellWirelessCtl).

Also make sure that your hardware switch is flipped on before using libsmbios and hid2hci.

---

### Post by manix user on 2009-02-06
I alredy have libsmbios installed, but hid2hci doesn't detect any devices. 
How exactly do I use lbsmbios to enable the bluetooth?

---

### Post by superm1 on 2009-02-06
dellWirelessCtl is the tool you are looking for

```
sudo dellWirelessCtl --info
```

will tell you how things are looking.

---

### Post by FoH on 2009-02-07
It could also be that you have to enter the bios and set the kill switch to control all radio functions (wifi, cell and bt). I don't think that you need to activate it from Windows. The only thing that might have to be activated from within Windows is the Wi-Fi catcher.

Also, Blueman is a great app for handling bluetooth devices. You can find it here: [http://blueman-project.org/](http://blueman-project.org/)

---

### Post by manix user on 2009-02-07
Tell me if I got it right:

dellWirelessCtl is a binary that comes with libsmbios, but the version of libsmbios in the ubuntu repository doesn't have it, so I have to download and compile the latest version then run **dellWirelessCtl --info**.

---

