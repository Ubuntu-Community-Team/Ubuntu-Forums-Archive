---
title: "Automatic mount of devices different under xfce and ratpoison"
date: 2008-11-15
forum: Desktop Environments
---

### Post by sbaboc on 2008-11-15
Hi all,
I have installed xubuntu intrepid on my dell latitude x1, gdm disabled so I use ratpoison (with startx) as my desktop (maybe this term is inappropriate).
Thunar works well into ratpoison, however it cannot mount some devices: some usb keys as well as my sd card, but mounts those without a problem when xfce is launched instead.
Under ratpoison I get this error message:

[I]hal-storage-mount-removable no <--(action,result)
[/I]
Any help welcome!

---

### Post by sbaboc on 2008-11-26
Hi all,
After some days I have noticed that if I start xfce without gdm (by startxfce4) I encounter the same problem I have with ratpoison, so automatic mounting of devices is launched by gdm; but I don't know how and I wish to have the same behavior with startx.
Is it possible?
tia

---

### Post by mali2297 on 2008-11-26
Is the HAL daemon running?
You can check with the command
```

pgrep -l hal

```

I assume that you have enabled the volume management in Thunar?

Also, try starting Thunar in daemon mode:
```

Thunar --daemon

```

---

### Post by sbaboc on 2008-11-26
Martin:
Is the HAL daemon running?

Yes

Running 
Thunar --daemon

is strange because it doesn't start thunar afaict, but if I start thunar after that things seem to improve : my usb key is mounted (actually one partition is), but my SD card still cannot be mounted.

Thanks (still hoping...)

---

### Post by mfrag on 2009-08-29
Any luck with this?  I'm having the same troubles...

---

### Post by hrod beraht on 2009-09-11
Install **thunar-volman**
In file manager preferences, go to the *advanced* page and check *enable volume management*.
Then check what you want on this screen:
[img]http://thunar.xfce.org/documentation/C/images/removable-drives-and-media.png[/img]

Bob

---

