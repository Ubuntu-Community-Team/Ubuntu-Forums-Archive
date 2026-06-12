---
title: "How to set persistent brightness in xubuntu?"
date: 2011-12-26
forum: Desktop Environments
---

### Post by kholis on 2011-12-26
Xfce4-brightness-plugin seem not save user's brightness setting. So I have to set the brightness every time after rebooting.

Any clue?

Thanks.

---

### Post by kholis on 2012-01-26
I added following commands in /etc/rc.local
```

echo 2 > /sys/class/backlight/acpi_video0/brightness
echo 2 > /sys/class/backlight/acpi_video1/brightness 

```

You can choose brightness value from 0-10

---

### Post by tommo1982 on 2012-05-02
I'm resurrecting an old thread, but you'd thinnk they fixed this issues a long time ago. This is not true. I am having the same problem with brightness restored to maximum value after system boot. The above solution is nice, but it won't fix my problem if I choose to change it one day and forget where I set it.

Does anyone know how to force Xfce to remember the brightness setting, without resorting to editting config files which sooner or later I forget?

The other issue is bluetooth which I have to turn off every time I start the system. Forgetting user brightness setting is not the only thing Xfce tends to 'forget'. Xubuntu is nice and all, but this little thing is really pissing me off.

---

