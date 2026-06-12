---
title: "GNOME does not start"
date: 2008-12-29
forum: General Help
---

### Post by Masquerade on 2008-12-29
Hey everyone.
Yesterday morning, i booted my computer like everytime. As i wanted to log into GNOME, the display flickered and i fell back to the login screen.

My xorg.conf looks like this:
```

Section "Monitor"
	Identifier "Configured Monitor"
	DisplaySize 322 241
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "Configured Video Device"
	Monitor "Configured Monitor"
	DefaultDepth	24
EndSection

Section "Device"
	Identifier "Configured Video Device"
	BusID "PCI:1:0:0"
	Driver	"nvidia"
EndSection

```

Can anyone help me with this?
thanks a lot
benny

---

### Post by eBoxNet on 2008-12-29
did you try to reconfigure your x?

---

### Post by gjoellee on 2008-12-29
Try an xfix, read how here: [http://kshoster.net/content/howto-run-xfix](http://kshoster.net/content/howto-run-xfix)

---

### Post by Masquerade on 2008-12-29
I did. several times. I even tried it with older backups of my xorg.conf that used to work.

---

