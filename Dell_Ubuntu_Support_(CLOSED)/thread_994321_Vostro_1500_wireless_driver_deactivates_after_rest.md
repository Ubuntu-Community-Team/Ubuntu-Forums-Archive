---
title: "Vostro 1500 wireless driver deactivates after restart"
date: 2008-11-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ebtoulson on 2008-11-26
hey I was just wondering if anyone knows how to fix this. Ever since I upgraded to 8.10 my wireless is deactivated upon start up it works fine if i go into hardware drivers and activate it but as soon as i restart its deactivates again. 

Thanks for your help.

---

### Post by adult swim on 2008-11-27
what driver are you using for your card and did you ever have to follow any tutorials to get it to work?

---

### Post by Ebtoulson on 2008-11-30
Thanks for the reply and sorry for the delay, was home for thanksgiving. 

I'm using the broadcom b43 wireless driver...um as far as a tutorial I did a long time ago so I don't remember where/what it was. Under windows wireless drivers it say I'm using bcmwl5.

---

### Post by adult swim on 2008-12-02
post the output of ```
cat /etc/modprobe.d/blacklist
```

---

### Post by Ebtoulson on 2008-12-02
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

blacklist b43
blacklist b43legacy
blacklist ssb

blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx

```

---

### Post by adult swim on 2008-12-02
there is your problem, probably some leftover blacklisted things from a tutorial you have followed before, two of them being the driver you are wanting to use.  you need to press alt+F2 and run ```
gksudo gedit /etc/modprobe.d/blacklist
``` at the end you can delete all of these ```
blacklist b43
blacklist b43legacy
blacklist ssb

blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
```
but add this one back
```
blacklist bcm43xx
```
close and save the file and your wireless should start after booting.

---

### Post by Ebtoulson on 2008-12-03
Hmm that didn't seem to work. I saved then rebooted and it was still disabled. Opening back up the hardware drivers it shows the gray circle beside broadcom b43 wireless driver and when I click activate it says "this driver was just disabled, but is still in use".

---

### Post by adult swim on 2008-12-03
does it turn on when you run 
```
sudo modprobe b43
```

---

### Post by Ebtoulson on 2008-12-03
yes it does

---

