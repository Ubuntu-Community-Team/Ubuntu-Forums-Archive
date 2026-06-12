---
title: "Ubuntu Wayland 20.04 laggy, unresponsive - 100 % CPU load gnome-shell"
date: 2020-09-30
forum: Desktop Environments
---

### Post by pppppppppppppppppp on 2020-09-30
After login into Ubuntu Wayland gnome-shell uses all my CPU load when moving mouse or typing smth:
[http://q4rockz.selfhost.co/specs/Pictures/Screenshot%20from%202020-09-30%2016-51-53.png](http://q4rockz.selfhost.co/specs/Pictures/Screenshot%20from%202020-09-30%2016-51-53.png)

When not typing:
[http://q4rockz.selfhost.co/specs/Pictures/Screenshot%20from%202020-09-30%2016-51-43.png](http://q4rockz.selfhost.co/specs/Pictures/Screenshot%20from%202020-09-30%2016-51-43.png)

uname -a
```
Linux toni-06 5.4.0-48-generic #52-Ubuntu SMP Thu Sep 10 10:58:49 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```

I have not installed any extensions.

Other specs like **hwinfo**, **lsusb**, **strace **etc. you can find here (included logs like **journalctl**, **dmesg **...):
[http://q4rockz.selfhost.co/specs/](http://q4rockz.selfhost.co/specs/)

---

### Post by similar2 on 2020-10-01
Do you see the same issue with different kernel versions?

---

### Post by deadflowr on 2020-10-01
Please don't post large images to the forums, either post a link to the images hosting site,
or use the forums attachments feature.
We ask because not everyone has the bandwidth or speed to load pages quickly with large images.

That said,
Your gpu is too weak to run Ubuntu Desktop.

Not sure how that helps, but it's something i see.

---

### Post by pppppppppppppppppp on 2020-10-01
I did not try other kernels.
Sure, GPU onboard is weak - but it can handle Xfce Desktop or plane Ubuntu desktop.
When i first used GDM instead of lighdm the login screen was also unresponsive in the same way like wayland.

---

