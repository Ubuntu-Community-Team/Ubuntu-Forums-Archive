---
title: "Additional Drivers NVIDIA This driver is activated but not in use"
date: 2011-05-30
forum: Desktop Environments
---

### Post by 08x on 2011-05-30
As the title says,

Attached an image for clarification

Ubuntu 11.04 64bit

Thanks in advance

Pete

---

### Post by baarn on 2011-05-31
having the same problem.
i am using a thinkpad with dual gpu btw, i believe there was a problem with intel optimus and linux, not sure if you have a laptop too, but that might be it.

---

### Post by wildmanne39 on 2011-05-31
> **baarn said:**
> having the same problem.
i am using a thinkpad with dual gpu btw, i believe there was a problem with intel optimus and linux, not sure if you have a laptop too, but that might be it.
Hi, as long as you activate the driver it is in use that is a bug that shows its not, if you have the unity desktop with the launcher on the left of the screen that is proof other wise you would have to boot ubuntu classic.

---

### Post by zanzibarwinds on 2011-05-31
Same issue for me.

After installing the drivers I clicked Activate and restarted ubuntu 11.04 but "Additional drivers" says its activated but not in use.

I've also changed the desktop to uBuntu Classic for the Gnome desktop is that is at all relevant.

Wanted this specifically for the Apperance -> Visual Effects tab to enable Wobbly Windows but the Visual Effects tab is unavailable and can only assume its because of the drivers not been in use.

Any help in this regard would be appreciated.

Regards and TIA
John

---

### Post by maverick280857 on 2011-05-31
Are you able to execute

```
nvidia-settings
```

Assuming that you want the driver mainly for compiz and wobbly windows, etc. you can just use the driver directly from NVIDIA.

---

### Post by baarn on 2011-05-31
i'm not using unity, i am on xubuntu actually... for me its not about optical desktop crap its more for openGL and openCL coding. but mainly its about getting my laptop work propperly ;)

nvidia-settings told me to start nvidia-xconfig... i did that yesterday and afterwards i had to trash that users account, wasn't usable anylonger...
glxinfo and glxgears shows something like this:
```
Xlib:  extension "GLX" missing on display ":0.0".
```

---

### Post by maverick280857 on 2011-05-31
> **baarn said:**
> i'm not using unity, i am on xubuntu actually... for me its not about optical desktop crap its more for openGL and openCL coding. but mainly its about getting my laptop work propperly ;)[/CODE]

Just get the drivers directly from NVIDIA, and install them instead of the restricted drivers.

---

### Post by wojox on 2011-05-31
Open a terminal and run:

```
sudo apt-get update; sudo apt-get install nvidia-common
```

Reboot.

---

