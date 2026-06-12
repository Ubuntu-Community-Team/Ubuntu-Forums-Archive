---
title: "Unable to increase screen resolution/ activate desktop effects"
date: 2009-02-27
forum: General Help
---

### Post by Aiello on 2009-02-27
Hey (sorry if this is in the wrong section!),

I just installed Ubuntu 8.10 on my friend's computer and we seem to be having some issues. Although the optimum screen resolution for his computer is 1280 x 1024 @ 60Hz, yet it only displays at 640 x 480 @ 75Hz. Furthermore, no desktop effects can be activated. I was thinking that maybe a restricted driver needs to be enabled, but the "Hardware Drivers" app can't find any. I am afraid my friend does not know what type of graphics card is in his computer.

At the moment the screen is horrible cramped and is EXTREMELY difficult to use, any suggestions would be greatly appreciated!

Thanks!

---

### Post by entr3p on 2009-02-27
Go to System -> Administration -> Hardware Drivers. It seems you guys need to activate your graphics card driver.

---

### Post by abyssius on 2009-02-27
> **Aiello said:**
> Hey (sorry if this is in the wrong section!),

I just installed Ubuntu 8.10 on my friend's computer and we seem to be having some issues. Although the optimum screen resolution for his computer is 1280 x 1024 @ 60Hz, yet it only displays at 640 x 480 @ 75Hz. Furthermore, no desktop effects can be activated. I was thinking that maybe a restricted driver needs to be enabled, but the "Hardware Drivers" app can't find any. I am afraid my friend does not know what type of graphics card is in his computer.

At the moment the screen is horrible cramped and is EXTREMELY difficult to use, any suggestions would be greatly appreciated!

Thanks!

You need to open a terminal and enter the following line:
```
sudo lshw -C display
```

This will identify your video hardware. There's not much that can be done until you share this information.

---

