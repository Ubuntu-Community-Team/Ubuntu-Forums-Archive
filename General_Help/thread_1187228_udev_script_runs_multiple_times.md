---
title: "udev script runs multiple times"
date: 2009-06-14
forum: General Help
---

### Post by AZzKikR on 2009-06-14
Hi guys,

I've been creating a udev rule + script to make it automatically backup a usb thumb drive of mine, when it's inserted. The rule matches my drive perfectly, and yay, my script is run as well. One problem though: it seems to run about 12 times when I insert my thumb drive! 

Is this normal behaviour, and is there any way how I can make sure the script is only run once? I know I can somehow fix it by using a lock-file, but I am looking for a solution within the udev part, if it exists.

Any ideas?

---

### Post by WarWizard89 on 2009-07-07
I don't know if I can be much help, but I'm having the same problem. I created this udev rule in a file called 93-usb-sync.rules

```
ATTRS{serial}=="899801162008011514250B77", ACTION=="add", RUN+="/usr/bin/usb-sync.sh"
```

It runs my script maybe about 14 times. It first started doing it when I added the serial match in there.

---

### Post by WarWizard89 on 2009-07-07
Alright, I think I got this down.

I took a look at the output of udev with this
```
udevadm monitor --udev
```
I saw exactly 14 events that had add in them.

I don't know a lot about how udev works, but it seems to go through some sort of hierarchy where your device inherits properties from parent devices. Anyway, by being more specific in my udev rule I limited it to only running once.

For reference here's my revised rule.
```

KERNEL=="sd*1", SUBSYSTEMS=="usb", SUBSYSTEM=="block", ATTRS{serial}=="899801162008011514250B77", ACTION=="add", RUN+="/usr/bin/usb-sync.sh"
```
And remember not to put any new lines in there.

AZzKikR if you posted your udev rule it's be helpful to diagnose the problem.

---

### Post by AZzKikR on 2009-07-17
Thanks for the reply. Being more specific in the udev rule actually seems like a feasible solution. I will try it out as soon as I can, and will let you know the results.

---

