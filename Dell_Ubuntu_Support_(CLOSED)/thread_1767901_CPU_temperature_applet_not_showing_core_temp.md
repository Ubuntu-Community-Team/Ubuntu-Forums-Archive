---
title: "CPU temperature applet not showing core temp"
date: 2011-05-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by manadi on 2011-05-26
Hi, 

I have installed lm-sensors according to this 

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

I am able to see the temperature on command line but the applet in the panel does not show CPU temperature, only HDD temp. 

Any ideas?
I am using Ubuntu 11.04 on Dell Inspiron 1525.

Thanks in advance.

---

### Post by psusi on 2011-05-26
Right click on the applet and go into the preferences and enable the other sensors.

---

### Post by manadi on 2011-05-27
Cant do that. When I choose "Kernel i2c sensors" or "Kernel i2c sensors(hwmon)" it says no thermal zones available and a red cross mark appears.

---

### Post by psusi on 2011-05-29
Is this a recent P4 cpu?  If so, load the p4 temp driver:

sudo modprobe pkgtemp

---

### Post by manadi on 2011-06-01
No its an old CPU. Centrino. This used to work on 10.10

---

### Post by psusi on 2011-06-02
Try pkgtemp

---

