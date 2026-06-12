---
title: "sensors-applet fail to display hd temp after kernel upgrade"
date: 2010-06-30
forum: Desktop Environments
---

### Post by reloweb on 2010-06-30
After Kernel upgrade, sensors-applet doesn't display the hd temp. To fix the problem I have to remove and after reinstall hddtemp package... :mad:

---

### Post by endotherm on 2010-06-30
try rerunning ```
sudo sensors-detect
```. it loads some kernel modules that are required for sensor access and potentially hddtemp as well. see if it works for ya

---

### Post by reloweb on 2010-06-30
No, I've just tried it but it doesn't work... The only solution is reinstall hddtemp everytime I upgrade kernel.

---

### Post by endotherm on 2010-06-30
that sucks. did you enter 'yes' on the last question in the dialog? it defaults to 'no', so  I've missed it a few times.

---

### Post by reloweb on 2010-06-30
Yes on the bottom of my /etc/modules there are this lines:
```
# Chip drivers
coretemp
it87
```

Moreover if I do sudo hddtemp /dev/sda it outputs me the right temp!
```
sudo hddtemp /dev/sda
/dev/sda: ST31500341AS: 56°C
```

---

### Post by stinkeye on 2010-07-04
I just had the same problem.
Running
```
sudo dpkg-reconfigure hddtemp
```
fixed it for me.
I just answer yes to all the questions.

---

