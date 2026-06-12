---
title: "Can't increase resolution (Solved)"
date: 2005-11-06
forum: Desktop Environments
---

### Post by aaronshaf on 2005-11-06
I for some reason cannot increase the screen resolution in ubuntu. I suspect it cannot recognize my monitor? Where do I go from here?

Thanks for your help,

Aaron

---

### Post by aysiu on 2005-11-06
You go [here](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by kairu0 on 2005-11-06
You probably have a problem in your /etc/X11/xorg.conf.

Try the text-based wizard (sudo dpkg-reconfigure xserver-xorg) to double-check your video card, monitor, and resolution settings.

If that doesn't work, open /etc/X11/xorg.conf by hand and check the resolution statements.


Oops he beat me to it :P

---

### Post by aaronshaf on 2005-11-06
Thanks. Worked.

---

