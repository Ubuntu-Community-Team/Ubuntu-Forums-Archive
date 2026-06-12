---
title: "few problems after minimal cd installation"
date: 2009-06-15
forum: General Help
---

### Post by pacman401 on 2009-06-15
Hello
I have ubuntu 9.04 installed using minimal cd.

# after installation I can't switch to or between virtual consoles by ctrl+alt+F1/F2/F3/F4/F5

# ctr+alt+backspace isn't restarting X

# my monitor is blanking/turning off but my xorg.conf isn't telling me nothing about that and i haven't installed any environment power managing program 
here how my /etc/X11/xorg.conf is presenting
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

---

