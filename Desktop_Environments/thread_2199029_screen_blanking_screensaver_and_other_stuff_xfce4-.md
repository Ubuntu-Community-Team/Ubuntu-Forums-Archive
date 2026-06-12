---
title: "screen blanking screensaver and other stuff xfce4-power-manager"
date: 2014-01-11
forum: Desktop Environments
---

### Post by marinara on 2014-01-11
Using Lubuntu 13.10 is a pleasure, but the screensaver (or power saving) settings have been a little wierd.
[URL="http://ubuntuforums.org/showthread.php?t=2197835&p=12893386#post12893386"]
this post[/URL] suggests doing it in the "default applications for lxsession"

What i've found is that you need to create a new file:

~/.config/lxsession/Lubuntu/autostart
you will need to add a few things.  begin each line with @
```

#start the power manager because 13.10 doesnt enable it by default
@xfce4-power-manager
```

```
#turn x.org default screensaver off because we are using the xfce4 power manager
@xset s off

```

finally logging out doesn't seem to work 100%.  I really don't understand why I have to reboot... but, reboot and you should be able to configure your screen blanking with the xfce4 power manager (in the start menu) instead of having x.org blank your screen.  Also i like the xfce4 power manager battery management.

verify xfce4 is running with: (pgrep returns a pid) ```

$pgrep xfce4-power- -lf
```
verify xorg screensaver is off with (last line should be "timeout: 0" )```

$xset q|grep Screen -C2 

```
FYI 13.10 doesn't have an animated screensaver.  If you want that you will have to install a screensaver, but I do not provide instructions here.

Chers!

---

### Post by sudodus on 2014-01-12
I would like to add a link to a bug report about locking and screensaving in Lubuntu 13.10.

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1205384](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1205384)

See the posts by [Jarno Suni]("https://launchpad.net/~jarnos")

---

### Post by Moliere on 2014-01-24
I love you! Man, I've been trying to fix this problem for weeks - yours is the only solution that actually works! I was on the verge of uninstalling Lubuntu - thank-you thank-you thank-you!

---

