---
title: "Removed KDE4 now gdm not working"
date: 2008-07-24
forum: Desktop Environments
---

### Post by jc750kwak on 2008-07-24
I'm on Hardy Heron. I tried KDE4 but it kept locking my display so I removed it using synaptic to remove all packages with kde4 in their title.

I had also set kde4-kdm as my default display manager. Now KDE4 has been removed gdm does not come up. All I get is a shell. Trying to start gdm from this shell results in a "Can't load display" error. I have gdm installed.

What shall I do next? I tried sudo dpkg-reconfigure xserver-xorg but that just asked me questions about my keyboard and mouse. I have searched these forums for "gdm not working" but without success.

Best regards

John

---

### Post by Tim Sharitt on 2008-07-24
Try
```
sudo dpkg-reconfigure gdm
```

---

