---
title: "XGL on Dapper and 7600gt"
date: 2006-06-10
forum: Desktop Environments
---

### Post by Attila_fdd on 2006-06-10
I have a pc with this configuration:
Opteron 146
Asrock 939sli32
1gb ram
7600gt

3d acceleration with opensource drivers nvidia-glx doesnt work,
3d acceleration with official nvidia drivers works.

So I can try to run XGL only with official nvidia drivers.

I have added the repository needed for compiz and xgl
and i have installed these packages: compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

After that i have updated the system.



I have changed the xorg.conf

the changes are:

> 
...
Section "Module"
	Load	"bitmap"
	Load	"ddc"
	# Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
...
Section "Device"
	Identifier	"NVIDIA 7600GT"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
	VideoRam	256000
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
EndSection
...
Section "Extensions"
        Option  "Composite" "Enable"
EndSection



and the  gdm.conf-custom
the changes are:

> 
...
[servers]
0=Xgl

[server-Xgl]
    name=Xgl server
    command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
    flexible=true



I did the script startcompiz in /usr/bin with these lines:

[quote=/usr/bin/startcompiz]
killall gnome-window-decorator
wait

DISPLAY=:0 compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
DISPLAY=:0 gnome-window-decorator &
xmodmap /usr/share/xmodmap/xmodmap.it &
[/quote]

I have added the script to the programs booted with session.

After reboot i was logged in, the system loaded the session but he came back to the login screen :(

---

### Post by Attila_fdd on 2006-06-11
up

---

### Post by Attila_fdd on 2006-06-12
up

---

