---
title: "Unable to set screen resolution in Jaunty"
date: 2009-04-28
forum: General Help
---

### Post by purbeck on 2009-04-28
Hi all,

Just moved from Suse to Kubuntu for various reasons, so am slowly coming to terms with the different ways things are done. The one that's got me stumped at the moment is how to get nvidia-settings to recognise my screen and provide acceptable settings options?

When I run it, I get a limited range of resolution options, which does not include 1280x1024 (which is what I want, of course). How can I get the H & V Sync options set, and specify the correct resolution?

I have created an xorg.conf file manually which contains the necessary info, but this does not appear to be read when restarting, as nothing has changed. 

Any help or advice here would be much appreciated!

---

### Post by 762sks on 2009-04-28
is it an nvidia card or ati?

---

### Post by purbeck on 2009-04-28
I have an nvidia GeForce 6100, which is easily capable of displaying at 1280x1024.

---

### Post by 762sks on 2009-04-28
have you tried going to the system/administration/hardware drivers? 

try that and then you should be able to change to a better driver. 

oncew you change the drivers try going to the nvidia x server video setting and set them. dont forget to save it to the config file but youll have to sudo the actuall file in order to save it here is the command to open it up

sudo nvidia-settings 

try that.

---

### Post by abn91c on 2009-04-28
In** [COLOR="blue"]kubuntu[/COLOR] **it is Applications>system>hardware drivers, check there for any drivers that need to be activated.[COLOR="Blue"][COLOR="blue"][/COLOR][/COLOR]
in the same menu click on the [COLOR="Blue"]screen resize & rotate[/COLOR] icon and see what other options you get.

---

### Post by purbeck on 2009-04-28
I've tried that, and am currently using the nvidia release 180, which is recommended. nvidia-settings gives me an option of 1152 or 1360 but no 1280.

And I can't work out why the xorg.conf file is not being read - but it clearly isn't. The file has a label to identify the device Model as "LG Flatron", but the only Model nvidia-settings reports is "CRT-0(CRT-0 on GPU-0)"

There's no Screen size & rotate under the Hardware Drivers, but under System Settings - Display I get the following options:
Size: 1152x864 plus a menu of lower resolutions, Refresh options of 63.0 or Auto, Orientation = No rotation (no other option shown.

Edit - oops, see where you mean now - but having run it, the data is as above.

---

### Post by joesapo on 2009-04-30
Same issue on Ubuntu.  This worked:

> **kpkeerthi said:**
> Enter this command in the terminal and reboot.
```
sudo nvidia-xconfig
```

---

