---
title: "Xubuntu - Wallpaper for dual monitors appears only after logout/login"
date: 2013-04-20
forum: Desktop Environments
---

### Post by Elfy on 2013-04-20
I've got 2 monitors running, .screenlayout/screens.sh works fine to set them up for me.

When I login, often I am left with the wallpaper showing in monitor 1 at some odd resolution.

Logout and then login will then have both monitors showing wallpaper filling screens.

Tried adding sleep to the randr script that runs which made no difference to that.

---

### Post by brainwash on 2013-04-20
Instead of relogging you could try to reload xfdesktop:
```
xfdesktop --reload
```

So generally it looks like you have to start xfdesktop _after_ the custom script has set up your monitors.

---

### Post by Elfy on 2013-04-20
Tried that - doesn't help I'm afraid.

---

### Post by matt_symes on 2013-04-20
Hi

Edit the file.

```
/etc/lightdm/lightdm.conf
```

add these two lines to the bottom.

```
display-setup-script=/path/to/script.sh 
session-setup-script=/path/to/script.sh
```

Kind regards

---

### Post by Elfy on 2013-04-20
I did that - you know I did :p


added to bottom of .conf

```
# login 
display-setup-script=/usr/share/screens.sh
#desktop session
session-setup-script=/usr/share/screens.sh
```

A bunch of reboots later and that appears to have done the trick.

---

