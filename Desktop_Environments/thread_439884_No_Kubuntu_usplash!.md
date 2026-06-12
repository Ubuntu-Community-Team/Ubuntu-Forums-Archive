---
title: "No Kubuntu usplash!"
date: 2007-05-11
forum: Desktop Environments
---

### Post by rich.bradshaw on 2007-05-11
I switched from Ubuntu to Kubuntu by installing kubuntu-desktop, and uninstalling everything in ubuntu-desktop. Now when I boot I don't get a usplash (the graphical ubuntu logo whilst it's booting/shutting down). I have the files

/usr/lib/usplash/usplash-theme-kubuntu.so

/usr/lib/usplash/usplash-artwork.so

and have tried regenerating initramfs

sudo dpkg-reconfigure linux-image-$(uname -r)

but nothing has worked... any ideas?

Thanks!

---

### Post by Psicolonia on 2007-05-11
look for a debian package of "startup-manager" and install it. then run it and set your usplash. that did iy for me! to teste it wrie "sudo usplash -c"

---

### Post by rich.bradshaw on 2007-05-11
Cheers, that seems to have worked - wonder how you do that manually though...

---

### Post by aralbald on 2007-05-14
It seems that after a complete uninstall of the ubuntu-desktop, and then - installation of kubuntu-desktop something goes wrong. If you take a closer look at the file /etc/alternatives/usplash-artwork.so:
```

#ls /etc/alternatives/usplash-artwork.so
/etc/alternatives/usplash-artwork.so -> /usr/lib/usplash/usplash-theme-ubuntu.so

```
you'll notice that it is a symbolic link to the file /usr/lib/usplash/usplash-theme-ubuntu.so (or whatever your currently configured usplash theme is). There is also another symbolic link -/usr/lib/usplash/ usplash-artwork.so -> /etc/alternatives/usplash-artwork.so, but as you can see it's pointing towards other symbolic link, so you can leave that alone.

So to manually set the usplash theme, if it's not working after installing usplash-theme-kubuntu (or whatever usplash artwork theme), you can do this:

```

sudo rm /etc/alternatives/usplash-artwork.so
ln -s /usr/lib/usplash/usplash-theme-kubuntu.so /etc/alternatives/usplash-artwork.so

```

After that reinstall the kubuntu usplash artwork:
```

aptitude reinstall kubuntu-artwork-usplash

```

Reboot and enjoy your usplash theme.

---

