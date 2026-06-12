---
title: "Customizing buttons xinput2"
date: 2016-03-21
forum: Desktop Environments
---

### Post by lukasz20 on 2016-03-21
I am using mouse which middle button is in not convenient place so I mapped wheel left tilt to middle button:
```
xinput set-button-map 'Logitech Unifying Device. Wireless PID:1017' 1 **6** 3 4 5 **2** 7 8 9 10 11 12 13 14 15 16
```

it seems that this method is now deprecated for the new applications, which are using newer method. I am affected by problem described in [this bug]("https://bugs.chromium.org/p/chromium/issues/detail?id=582547") - Chrome is not obeying the setting from xinput.
There is a lot of manuals how to reverse scroll direction using new method (with set prop), but I didn't find information how to map buttons.

I also tried with xmodmap:
```
xmodmap -e "pointer = 1 6 3 4 5 2 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24"
```

In both cases tilt left is not behaving correctly in chrome, while it is working perfectly fin in other applications.

---

### Post by bbouwens on 2016-06-29
Same problem here, still looking for a solution.

---

