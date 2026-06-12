---
title: "System settings menu Wierd GUI and loss of some funtions..."
date: 2018-02-03
forum: Desktop Environments
---

### Post by messiah5150 on 2018-02-03
Hi All;

So I did something stoopid,
I noticed that evolution was loaded about 4 or 5 times in my system monitor. I don't use evolution mail, calendar etc so I figured I'd dump it.
I went into the terminal (1st mistake) and typed in: sudo apt-get purge evolution* (2nd mistake)
Now, my system settings looks and functions weird. Also, some of my panel indicators at all gone. Also, system settings won't load from there or "about this computer".
So obviously I've done something silly and its clear that perhaps portions of the software are used by Ubuntu 16.04.
Is there a way to fix this easily? Or am I doing a wipe and re-load?  I've recognize my mistake but not researching first (bad user...)
I tried to reinstall evolution* hoping that would help...but clearly, I'm missing something all together.

Ubuntu 16.04.3 LTS
Lenovo T430s
i5 3320m
8gb DDR3
480gb SSD
Nvidia NVS5200m

Thanks for any insight, help, yelling at noobish mistake etc....

Darryl

---

### Post by again? on 2018-02-03
Try ```
sudo apt install -s ubuntu-desktop
```
This is just a simulation (-s) and will show what will happen without actually doing anything.

If your happy with what will occur, remove the -s option.
```
sudo apt install ubuntu-desktop
```

---

