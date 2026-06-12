---
title: "Cadega, Nvidia and 3D acceleration?"
date: 2006-09-28
forum: Desktop Environments
---

### Post by BabyBoy on 2006-09-28
Hey I bought Cadega as wine didn;t play much of the games I wanted too,
Well I got it all up and running:

Cadega 5
Engine 5.2.3

And I can quite saftly say its BRILLIANT!! anyhow thats not my problem
when I start the game or do the tests it fails on the 3D acceleration which is why I think the game runs REALLY! slow.

I have a Gforce 2 MX 400 64MB, I took the liberty of taking a screen shot of the driver that is loaded on.

[http://img99.imageshack.us/img99/3900/screenshotzv3.png](http://img99.imageshack.us/img99/3900/screenshotzv3.png)

As you can see rendering works, and driver is loaded.

I would really appreciate any help to get 3D acceleration up and working.

Thanks,

---

### Post by BabyBoy on 2006-09-28
Just a little update:

when i type:

```
nvidia-glx-config enable
```

I get:

```
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

```

---

### Post by Jeremy23 on 2006-09-28
If you're getting a "Direct rendering: Yes" message, like you showed us, then your 3D acceleration is fine. Go and run ```
glxgears -printfps
``` and you'll see what I mean.

I suspect the problem lies elsewhere. It's interesting that the 3D test on Cedega fails. I have an NVIDIA GeForce2 MX 400 card as well and it works beautifully.

OpenGL games such as Quake3, Enemy Territory or World of Warcraft run on Wine. If you have any of those games, try running one of them in Wine and then trying it in Cedega. If it runs well in Wine but not in Cedega, it's probably a Cedega problem.

Unfortunately, Cedega is generally slower than running games natively on Windows, especially Direct3D. For example, I run Mafia on Windows XP at 1280x1024 and I get a decent framerate between 20-40 fps. On Cedega, I have to run it at 800x600 to get the same framerate.

If you've got a beefy internet connection, you can type ```
sudo apt-get install planetpenguin-racer
``` and that will install Planet Penguin Racer, a fun 3D accelerated game. You can use that to test that native Linux games are running properly.

BTW it's *Cedega*, not *Cadega* ;)

---

### Post by Jeremy23 on 2006-09-28
> **BabyBoy said:**
> Just a little update:

when i type:

```
nvidia-glx-config enable
```

I get:

```
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

```

Are you getting an NVIDIA logo before the login screen comes up on first boot? If so, the NVIDIA drivers are already loaded. A ```
glxinfo | grep rendering
``` will show you further evidence that they're loaded.

---

### Post by BabyBoy on 2006-09-28
Yeah I see what you mean... Wonder why 3D fails in cedega

```
nvidia-glx-config enable
```

Works fine when I just done it, It enabled :)

But still fails in Cedega and that penguin game runs VERY! nice.

---

