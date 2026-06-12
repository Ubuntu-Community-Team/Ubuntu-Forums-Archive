---
title: "is it possible to add 1440x900 resolution on Dell Inspiron 1525 Laptop"
date: 2012-08-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by IsraeliHawk on 2012-08-29
hello all,

I have a 5 year-old Dell Inspiron 1525 laptop, with a display resolution of 1280x800 (16:10). 

I wish to increase that resolution to at least 1440x900. 

Is this possible? If so - how? 

cheers

---

### Post by mikewhatever on 2012-08-29
It should be possible, and here is [an example]("http://techfrp.blogspot.co.il/2010/09/xrandr-desktop-scaling-for-ubuntu.html") of how it's done. There are many more test cases on the web, just search for 'virtual resolution' in case you need more info.

---

### Post by IsraeliHawk on 2012-12-30
> **mikewhatever said:**
> It should be possible, and here is [an example]("http://techfrp.blogspot.co.il/2010/09/xrandr-desktop-scaling-for-ubuntu.html") of how it's done. There are many more test cases on the web, just search for 'virtual resolution' in case you need more info.

thanks. 

tried - yet i fail for some reason. I mainly used [this thread]("http://ubuntuforums.org/showthread.php?t=1112186")

here's the log

```
ushabtay@ushabtay-Inspiron-1525:~$ xrandr | grep maximum
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
ushabtay@ushabtay-Inspiron-1525:~$ gtf 1440 900 59.9

  # 1440x900 @ 59.90 Hz (GTF) hsync: 55.83 kHz; pclk: 106.29 MHz
  Modeline "1440x900_59.90"  106.29  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

ushabtay@ushabtay-Inspiron-1525:~$ xrandr --newmode "1440x900_59.90"  106.29  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
ushabtay@ushabtay-Inspiron-1525:~$ xrandr --addmode VGA 1440x900_59.90
xrandr: cannot find output "VGA"
ushabtay@ushabtay-Inspiron-1525:~$ xrandr --addmode LVDS1 1440x900_59.90
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  29
  Current serial number in output stream:  30
ushabtay@ushabtay-Inspiron-1525:~$ 


```

---

