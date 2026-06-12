---
title: "screens not found xconfig broken"
date: 2008-01-10
forum: Desktop Environments
---

### Post by pfwd.tech on 2008-01-10
I was playing with the Xconfig file and I think its broken.

Both of my screens are not found.  They are both Black when the login screen comes on. (I can hear the login drum sound).

Is there any way of accessing the xconfig file via the boot recovery screen?

My graphics card is a Nvidia 6200.

---

### Post by taurus on 2008-01-10
```
nano -Bw /etc/X11/xorg.conf
```
Save it with <Ctrl>o and exit with <Ctrl>x.

---

### Post by pfwd.tech on 2008-01-10
Great thanks.  Do you know where I could get an example xConfig file from?

---

### Post by taurus on 2008-01-10
You mean /etc/X11/xorg.conf?

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by pfwd.tech on 2008-01-10
yeah sorry thats what i meant.

---

