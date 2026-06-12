---
title: "Easy way to restore system?"
date: 2006-10-04
forum: Desktop Environments
---

### Post by Trifid on 2006-10-04
Basically, I am trying to install Beryl and XGL (with the Nvidia guide on here) and after 3 attempts and formats I am asking is there an easy way to restore the system? 

When it gets to the reboot bit it goes to the black and white command prompt screen, and then comes up with a blue screen

> X server not set up correctly....

Any ideas, or do I have to do a format (again)?

Thanks for the help (yet again.)

---

### Post by dyous87 on 2006-10-04
from the command line try reconfiguring x. 
```
sudo dpkg-reconfigure xserver-xorg
```

then just choose all your options and when its all done simply type in ```
startx
``` and see if that works.

---

### Post by Trifid on 2006-10-04
OK, I entered the first one and it started asking me questions about graphics card, OK. Then went onto keyboard and then onto mouse where it didn't have my option (USB) - is this meant to happen?

---

### Post by dyous87 on 2006-10-04
just make the whole thing go through until it gets to your resolution and monitor settings to see if that is autodetected. I wouldn't worry about the keyboard and mouse.

---

