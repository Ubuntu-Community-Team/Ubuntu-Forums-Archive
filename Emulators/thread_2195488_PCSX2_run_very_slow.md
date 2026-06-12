---
title: "PCSX2 run very slow"
date: 2013-12-24
forum: Emulators
---

### Post by gugu88 on 2013-12-24
**PCSX2 run very slow. ** 			
			 				Hi everyone!!!

I'm attempting to use pcsx2 1.0.0 on ubuntu 12.04 64 bit. I properly  completed the installation and I managed to start playing with two games  (final fantasy X and tekken 5). The only problem is that both the games  run very slow and with an awful graphic!!

I checked for the system requirements and I have more than the recomended!!

I have:
Intel® Core™ i5 CPU       M 460  @ 2.53GHz
NVIDIA GEFORCE GT 425M (2 GB)
RAM: 8 GB (1333)

I looked for configuration guides on google but most of them are written  for windows, then I am a beginner and can not understand the more detailed  ones!!

I tried to start pcsx2 from terminal and I get lots of errors.
```
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x3 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x2 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x2 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x8 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x3 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x2 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x2 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x8 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x3 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x2 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x2 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x8 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x3 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x2 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x2 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x8 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x3 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x2 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x2 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x8 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x3 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x2 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x2 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x8 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x3 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x2 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x2 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x8 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x3 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x2 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x2 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x8 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x3 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
ZZOgl-PG:  Failed to create 8192x1 texture.
ZZOgl-PG:  SetTexVariablesInt error.
`menu_proxy_module_load': pcsx2: undefined symbol: menu_proxy_module_load

(pcsx2:5708): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': pcsx2: undefined symbol: menu_proxy_module_load

(pcsx2:5708): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': pcsx2: undefined symbol: menu_proxy_module_load

(pcsx2:5708): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': pcsx2: undefined symbol: menu_proxy_module_load

(pcsx2:5708): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': pcsx2: undefined symbol: menu_proxy_module_load

(pcsx2:5708): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': pcsx2: undefined symbol: menu_proxy_module_load

(pcsx2:5708): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': pcsx2: undefined symbol: menu_proxy_module_load

(pcsx2:5708): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': pcsx2: undefined symbol: menu_proxy_module_load

(pcsx2:5708): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': pcsx2: undefined symbol: menu_proxy_module_load

(pcsx2:5708): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': pcsx2: undefined symbol: menu_proxy_module_load

(pcsx2:5708): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': pcsx2: undefined symbol: menu_proxy_module_load

(pcsx2:5708): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': pcsx2: undefined symbol: menu_proxy_module_load

(pcsx2:5708): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': pcsx2: undefined symbol: menu_proxy_module_load

(pcsx2:5708): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': pcsx2: undefined symbol: menu_proxy_module_load

(pcsx2:5708): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': pcsx2: undefined symbol: menu_proxy_module_load

(pcsx2:5708): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': pcsx2: undefined symbol: menu_proxy_module_load

(pcsx2:5708): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': pcsx2: undefined symbol: menu_proxy_module_load

(pcsx2:5708): Gtk-WARNING **: Failed to load type module: (null)

[0mReleasing host memory maps for virtual systems...


```

I am not able to recover previous messages from terminal but there were much more of them!!

Hope someone could help me!!!

Sorry for my terrible english...

---

### Post by kostkon on 2013-12-24
Make sure you are using the OpenGL driver (under Configuration -> Plugins & BIOS) and also there are tons of options under the Graphics settings.

---

### Post by gugu88 on 2013-12-26
I am using OpenGL. About the tons of options under Graphics Settings I wasn't able to find a good guido for linus users!! Do you know some good guide??

---

