---
title: "USB won't charge Cell phone"
date: 2007-07-26
forum: Desktop Environments
---

### Post by RandyNemo on 2007-07-26
I am running 7.10 and when I plug in my cell phone to connect to the desktop nothing happens..The charge light on my phone lights up for just a second and then goes off.  If I do a lsusb is shows up as a drive but will not connect or charge from the USB port.  I am using a Dell laptop D600.  Any help would be appreciated.

---

### Post by tgm4883 on 2007-07-26
Perhaps your phone will not charge via USB?  The cable may not be meant for charging.

---

### Post by geraldm on 2007-07-26
```

cat /proc/bus/usb/devices

```
The above command would show the power availability for the charger with any other
devices plugged in.
Does the charger only need the usb power line to charge, or was there a driver 
that the vendor was to supply for the charger?

---

### Post by RandyNemo on 2007-07-26
Thanks guy, but still does not work..It used to work with 7.04.  It has a mp3 built in and it doesn't even mount the 
phone to copy music to it.  The light flashes and then goes off.  LIke I said it used to work but now it doesn't

---

