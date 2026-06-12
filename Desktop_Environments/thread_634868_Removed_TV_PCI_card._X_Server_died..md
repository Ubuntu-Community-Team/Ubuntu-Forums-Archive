---
title: "Removed TV PCI card. X Server died."
date: 2007-12-08
forum: Desktop Environments
---

### Post by antiigrav on 2007-12-08
Hi

I removed my TV card (Fusion HDTV DVB-Plus).

Restarted computer.

X server failed. Went to a text-based screen where i could view details or choose ok. Choosing ok, then says x server disabled so settings can be repaired.

Restarting keeps returning to this screen. Placing the card back in did not fix the problem.

Dual booted to Windows now which is working fine.

How do i fix this please?

I assume TV card had this affect because it has video-in capture (which is a display component).

Thanks.

---

### Post by Tenken on 2007-12-08
My suggestion would be to reconfigure X. First backup your old copy of X just in case.

```
cd /etc/X11/
cp xorg.conf xorg.conf.backup
```

then reconfigure X

```
sudo X -configure
cp /root/xorg.conf.new /etc/X11/xorg.conf
```

I'm not 100% sure xorg.conf.new is the name, if not try

```
ls /root/x*
```

to find the proper name.

---

