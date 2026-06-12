---
title: "bad keyboard mappings when logging in remotely from MacBook"
date: 2007-07-10
forum: Desktop Environments
---

### Post by RockyMcNuts on 2007-07-10
I am running 7.04 Feisty on an Intel PC. When I log in locally the keyboard works great.

I was able to start a remote Gnome session from my MacBook shell using 

[FONT="Courier New"]/usr/X11R6/bin/X -query 192.168.x.x
[/FONT]
However in the remote session from the MacBook the keys are mismapped, ie

[FONT="Courier New"]qwertyuiop => -=<backspace><tab>wqdgsh
asdfghjkl  => a<no-op>1243l'k
zxcvbnm => 56780xc
[/FONT]

Googling around I tried adding Option "XkbModel" "mac" in xorg.conf under Section "InputDevice' but to no avail. 

In any event I'm not sure it's something I'd want to set globally, only when the MacBook logs into Gnome. An xterm session from the MacBook to Feisty works fine and of course logging in locally works fine.

Can anyone point me in the right direction as to what keyboard mappings I should use and how to specify them when starting up X with -query option?

Many thanks and cheers!

---

