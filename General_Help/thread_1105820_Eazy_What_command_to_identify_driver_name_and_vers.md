---
title: "Eazy: What command to identify driver name and version"
date: 2009-03-25
forum: General Help
---

### Post by Deathray on 2009-03-25
I am interested in seeing which driver my Alfa 500 mW wireless usb interface is using - which command should I issue to find out :) ? I know of modinfo - but what if I dont know the name of the driver :b ?

---

### Post by heindsight on 2009-03-25
You can install hwinfo:
```
sudo apt-get hwinfo
```

Then do either:
```
sudo hwinfo
```
To get a listing of all hardware (including the driver for each), or you can do:
```
sudo hwinfo --usb
```
to only get info about usb devices.

---

### Post by dcstar on 2009-03-25
> **Deathray said:**
> I am interested in seeing which driver my Alfa 500 mW wireless usb interface is using - which command should I issue to find out :) ? I know of modinfo - but what if I dont know the name of the driver :b ?

```
sudo lshw
```

---

### Post by Deathray on 2009-03-25
> **dcstar said:**
> ```
sudo lshw
```

Wow, powerful command! Thanks for the help guys :)

---

