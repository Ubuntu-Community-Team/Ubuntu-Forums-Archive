---
title: "/etc/modprobe.d/options in Jaunty?"
date: 2009-04-26
forum: General Help
---

### Post by atihip on 2009-04-26
I recently upgraded to 9.04 on my macbook 1.1 and in previous versions (8.04 and 8.10) I've had a few lines in my /etc/modprobe.d/options file, specifically the lines:

```
options processor max_cstate=2
options hid pb_fnmode=2
```

It seems that now instead of one options file there are several *.conf files. I created one with the options above named options.conf and ran:

```
update-initramfs -u
```

Upon reboot neither of the options have been passed successfully. Is there a different way to pass commands such as this in Jaunty? Any help would be greatly appreciated. Thanks!

---

### Post by spiderbatdad on 2009-04-26
I notice the upgrade turned mine into a file named "options.dpkg.bak" and a hidden "options~"
have you tried simply naming it options instead of options.conf?

---

### Post by atihip on 2009-04-26
Haven't figured everything out, but I was able to set the max_cstate by adding to my /boot/grub/menu.lst at the kernel line:

```
processor.max_cstate=2
```

Using either an 'options' or 'options.conf' file in /etc/modprobe.d did not remedy the situation.

---

