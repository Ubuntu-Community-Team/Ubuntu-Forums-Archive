---
title: "Lightdm not loading on boot [11.10]"
date: 2012-04-05
forum: Desktop Environments
---

### Post by fexar on 2012-04-05
A recurring problem I've been having since fresh install of Ubuntu 11.10 is that on boot LightDM does not start and instead I boot to tty. I have to log in, manually start lightdm then log in again at the greeter screen.

Previously, I was able to temporarily solve this by running

```
sudo /usr/bin/lightdm/lightdm-set-defaults --greeter=unity-greeter
```

until the next update would break it again. However, this no longer works; /usr/bin/lightdm/ no longer exists. I checked the lightdm.conf file in /etc/lightdm/ and unity-greeter is specified by default. I don't even know where to look to debug this issue, so if anyone has any suggestions I would be very grateful for the help.

Thanks for your time.

---

### Post by Bobhuber on 2012-04-06
> **fexar said:**
> A recurring problem I've been having since fresh install of Ubuntu 11.10 is that on boot LightDM does not start and instead I boot to tty. I have to log in, manually start lightdm then log in again at the greeter screen.

Previously, I was able to temporarily solve this by running

```
sudo /usr/bin/lightdm/lightdm-set-defaults --greeter=unity-greeter
```until the next update would break it again. However, this no longer works; /usr/bin/lightdm/ no longer exists. I checked the lightdm.conf file in /etc/lightdm/ and unity-greeter is specified by default. I don't even know where to look to debug this issue, so if anyone has any suggestions I would be very grateful for the help.

Thanks for your time.
lightdm resides in /usr/sbin if that will help you.

---

### Post by fexar on 2012-04-06
Thanks for the reply Bobhuber, but there's not much I can do with the /usr/sbin/lightdm module.

The settings are in /usr/lib/lightdm/ for lightdm-set-defaults, not /usr/bin/lightdm/ as I mistakenly typed above. However, whereas setting the greeter via terminal before would fix the issue (at least temporarily), it no longer does so and I boot to tty with no greeter. It's really frustrating to have to launch lightdm manually and log in twice.

If anyone has any suggestions, I'd happily entertain them. I've had no luck scouring Google or these forums and I've been searching for weeks now.

---

### Post by Bobhuber on 2012-04-06
Try this

sudo dpkg-reconfigure lightdm

---

### Post by fexar on 2012-04-07
Yields the error:

```
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_NAME missing
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_PACKAGE missing
```

---

### Post by Bobhuber on 2012-04-07
> **fexar said:**
> Yields the error:

```
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_NAME missing
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_PACKAGE missing
```
OK - Take a look here. Gonna get there yet.
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/854337](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/854337)

sudo su
echo "/usr/sbin/lightdm" > /etc/X11/default-display-manager
 exit

---

### Post by fexar on 2012-04-07
Excellent! That appears to be the solution I needed. Thank you so much for your help, Bobhuber.

---

### Post by fexar on 2012-04-10
Nevermind. While it temporarily provided a fix, I'm back to square one again. I checked the default-display-manager file and the reference is still there. But I'm booting into TTY once again. I haven't applied any updates since the change, but it did work on the initial reboot. It's as though some times it will boot to the greeter and other times it catches an exception and kicks back to term.

---

