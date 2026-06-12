---
title: "X won't work on new Feisty install :("
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by herbster on 2007-06-24
I just installed Feisty, then used Envy to install the drivers. I have a 7600 GS.

Everything worked, I got Twinview going as well. Then I rebooted and X wouldn't start, here's the log, error is right at the very end:

[http://pastebin.ca/587712](http://pastebin.ca/587712)

I have done
```
dpkg-reconfigure xserver-xorg
```

But it don't work. I don't think it's Xorg, but I'm not sure. Nothing seems to get it to work.

Please help :(

EDIT: I booted into Feisty and I can only use console from text login, so I just did:

```
sudo apt-get --purge remove nvidia-glx nvidia-glx-new nvidia-kernel-common nvidia-settings
sudo apt-get install nvidia-glx-new
```

And a reboot, and this is the log: [http://pastebin.ca/587752](http://pastebin.ca/587752) (again, the very end)

---

### Post by steveneddy on 2007-06-24
You uninstalled two video drivers for nvidia.

You can only have [COLOR="Red"]one video driver for nvidia installed at any one time[/COLOR].

```
dpkg-reconfigure xserver-xorg
```

again and choose the vesa driver. It is a safe driver.

Then 

```
sudo /etc/init.d/gdm restart
```

and go to synaptic and choose the nvidia-new driver and nvidia kernel headers.

CTRL+ALT+F1

```
sudo /etc/init.d/gdm stop
```

```
dpkg-reconfigure xserver-xorg
```

choose the nvidia driver choice, not nv.

```
sudo /etc/init.d/gdm restart
```

That should do it.

---

### Post by herbster on 2007-06-24
steveneddy,

Thanks for that, but I actually reinstalled Feisty, should've waited for your post ;)

However, I installed nvidia-glx-new and restarted, but nothing happens. How do I install the nvidia driver???

EDIT: Got it working, whew! I went to Restricted Driver Manager and enabled, rebooted and it pooped on me, same text login and X server crash, but I just did apt-get install nvidia-glx-new then and it works now :)

Regardless, thanks so much for the help steveneddy!

---

### Post by steveneddy on 2007-06-25
You're welcome.

---

