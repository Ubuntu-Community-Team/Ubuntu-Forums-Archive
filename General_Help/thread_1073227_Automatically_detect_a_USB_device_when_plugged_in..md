---
title: "Automatically detect a USB device when plugged in."
date: 2009-02-18
forum: General Help
---

### Post by linux_ubun on 2009-02-18
Hi,
I have installed Ubuntu 8.04 on my machine. 
I need to come up with a solution(C++ application or shell script) that automatically detects whenever a USB device is plugged into the USB port and automatically copy a file into it. How can this be done thru HAL or any other means ? 
I did come across a solution using the etc/rc.conf file but later found that it was possible only in Arch.:(
Can anybody please suggest a solution in Ubuntu 8.04 ?

---

### Post by sdennie on 2009-02-18
You can write a udev rule to do this.  You'll need to know some information about your device and then you can tell udev to run a script whenever it is plugged in.  Looking at the examples and how to identify devices in this guide should be what you are looking for: [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---

