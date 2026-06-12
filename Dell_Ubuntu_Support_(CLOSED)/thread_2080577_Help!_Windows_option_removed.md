---
title: "Help! Windows option removed"
date: 2012-11-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by KingArthurIII on 2012-11-04
I accidentally removed the windows option from windows bootloader, so I installed Ubuntu, hoping that GRUB would allow me to go straight to windows, but to no avail. Please offer any options you can to a _novice_. I have Windows 7, so I cannot simply edit boot.ini... I'm on Ubuntu 12.10

---

### Post by ugm6hr on 2012-11-04
You'll have to provide more detail of EXACTLY what you did, and what your current state is.

I realise you may be panicked, but spending a bit of time describing the events that led to your difficulties, and the attempts you made to correct them can be invaluable in making plans to correct them.

Additional important information:
1. Do you want to use Ubuntu at all?
2. Did you have Ubuntu installed alongside Windows in the first place?
3. How did you remove the Windows option from the Windows bootloader?
4. What was the original bootloader?
5. How did you install Ubuntu?
6. Can you boot into Ubuntu now?
If so - print output from:
```
sudo fdisk -l
```

---

