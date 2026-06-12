---
title: "gnome 3 werid display problem"
date: 2015-02-15
forum: Desktop Environments
---

### Post by daviesray on 2015-02-15
i have a werid problem on gnome 3 it looks werid?
and i use intel grapichs
[IMG]http://i.share.pho.to/bf48843c_o.png[/IMG][IMG]http://i.share.pho.to/fd7d3cf8_o.png[/IMG][IMG]http://i.share.pho.to/1956d3b3_o.png[/IMG]

---

### Post by kerry_s on 2015-02-15
press alt+f2
type-> gksudo gedit /etc/X11/xorg.conf
copy & paste:

```
Section "Device"
	Identifier "Intel Graphics"
	Driver "intel"
	Option "AccelMethod" "uxa"
EndSection

```

log out & back in to restart x

weird i only got that on ubuntu 15, trying the alpha
anyways hope that helps you, i always use it now cause intel switched to that new saa, very unstable.

---

