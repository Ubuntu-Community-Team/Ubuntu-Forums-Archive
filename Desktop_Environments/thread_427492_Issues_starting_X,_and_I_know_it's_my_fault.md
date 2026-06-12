---
title: "Issues starting X, and I know it's my fault"
date: 2007-04-29
forum: Desktop Environments
---

### Post by Modly on 2007-04-29
Last night I used my desktop box (Which I do have running a dual boot Ubuntu/windows setup) and a hard drive adapter to install Ubuntu on my laptop drive.  I don't have a CD drive for my laptop,  so I figured this would be an option to get an OS on it for now.

Well, obviously during the install it detected the video card that I've got in my desktop (GeForce 4400),  and when I boot up the laptop,  it gives me the "No screens found" error,  and in the detailed error list bit,  right after it shows a massive ton of GeForce video cards listed in the support for the driver I'm using,  it choked.

So,  how do I use the CLI to tamper with the video card settings?  I'm still fairly new to Ubuntu and the distros I've used before all had XFree86, which I'm not seeing in here.

---

### Post by taurus on 2007-04-29
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by dreadlord_chris on 2007-04-29
from the command line:
```

sudo dpkg-reconfigure xserver-xorg

```
When it asks for the driver - select **vesa**. Finish the options - make sure that you **only** mark the resolutions that you know you can use. This will set things up to use the *default* graphics driver and allow you to actually boot to a Desktop environment.
Once that's done:
```

sudo /etc/init.d/gdm restart

```
You should now get a graphical login screen.
Now you can figure out what GPU your laptop uses & install the proper drivers.

---

### Post by Modly on 2007-04-29
Thanks all,  that did the trick.

I'm now excited because I've had this laptop a month without an OS.

---

