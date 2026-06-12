---
title: "XFCE4 Power manager 1.0.11 bugs"
date: 2012-10-21
forum: Desktop Environments
---

### Post by Kotrfa on 2012-10-21
Hi,

I've just installed Xubuntu 12 on my laptop and I've couple of problems with xfce4-power-manager 1.0.11. It doesn't recognize when is cable unplugged (so it keep saying "charging") and it also displays two icons at my top bar - one of them is right - battery, the second one is just red circle - missing icon, but when I right click on it, it gives me same offer as the battery does. 
I tried to reinstall it, but it doesn't work. And I don't find any other power manager, which can be used instead of this one. 
Thanks

---

### Post by Toz on 2012-10-22
Hello and welcome to the forums.

Can you provide more information about your laptop? The make and model would be helpful. 

Also, can you open a terminal window, issue the following commands and post back the results:
```
ls /proc/acpi/battery
```
```
pastebinit /var/log/dmesg
```
...this will return a link where a copy of your dmesg log file will be uploaded to. Please post back this link so we can have a look at that log file.

---

### Post by Kotrfa on 2012-10-22
Thanks for answer.
My laptop is Samsung 530U (version with SSD disk). Today I reinstalled Xubuntu and the problem is still same.


Here is the output of pastebinit:

[http://paste.ubuntu.com/1298598/](http://paste.ubuntu.com/1298598/)

---

### Post by Toz on 2012-10-22
It looks like this is a known bug. Please refer to: [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/971061]("https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/971061").

---

