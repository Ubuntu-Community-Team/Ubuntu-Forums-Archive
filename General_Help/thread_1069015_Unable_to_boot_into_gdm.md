---
title: "Unable to boot into gdm"
date: 2009-02-13
forum: General Help
---

### Post by Sims12345 on 2009-02-13
I was playing around with splashy and it wasnt working right so I decided to uninstall. 

Now, when I boot, it says something like tty1 main process ended along with a login prompt. I login and it does the same thing (tty1 thing) 

So, I went into recovery mode and attempted a fsck as well as a dpkg ann an xfix. xfix returned the error "cannot create regular file, read only file system" and brought me back to recovery console

Next, I went into the root shell prompt and did ```
sudo /etc/init.d/gdm restart
``` which returned ```
Stopping GNOME Display Manager...
return: 24: Illegal number: Stopping
Starting GNOME Display Manager...
return: 24: Illegal number: Starting
```
and returned me to the root prompt

Finally, I tried ```
sudo gdm restart
``` which gave me a screen which said could not start the X server (graphical environment) due to some internal error...

Please help!

Thanks

---

