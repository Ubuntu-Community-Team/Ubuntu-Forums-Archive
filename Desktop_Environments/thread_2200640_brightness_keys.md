---
title: "brightness keys"
date: 2014-01-20
forum: Desktop Environments
---

### Post by cmcanulty on 2014-01-20
I run gnome classic no effects 12.04 64 bits Yesterday I had to do a system fix and noticed that in the xubuntu 13.10  live 64 bit system my brightness keys worked for the first time ever. So my question is there should be a way to may it work in classic since it is obvioiusly a software issue. It is an HP g72t laptop.

---

### Post by Toz on 2014-01-20
More than likely its the newer kernel in 13.10 that is making the brightness keys work (or possibly the video driver on the LiveCD). Try running these commands on both your 12.04 system and the 13.10 LiveCD:

1. Kernel boot line:
```
cat /proc/cmdline
```

2. Info about video card(s) and drivers:
```
lspci -k  |grep -A2 VGA
```

3. Recognized backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

Compare the differences.

---

