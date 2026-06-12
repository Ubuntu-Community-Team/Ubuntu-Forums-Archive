---
title: "Desktop Effects not available"
date: 2007-05-16
forum: Desktop Effects &amp; Customization
---

### Post by SikEnCide on 2007-05-16
ok well i have ubuntu dual booting on my laptop perfectly running berly and everything..

i installed it on my parents computer and installed teh restricted ATI driver and now i get this window popping up when i go to the desktop effects selection under preferances

[IMG]http://img.photobucket.com/albums/v222/jugganinja/ubuntu/Screenshot.png[/IMG]

---

### Post by gwoodard on 2007-05-16
Umm.... What is the model of your ATi Card? How much MB of Memory does it have and what is the speed of your computer?

---

### Post by Gus_T_Reer on 2007-05-16
I have an x850xt card with the restricted fglrx driver and an entry in the xorg.conf file reads 
Section "Extensions"
	Option		"Composite"	"0"
EndSection

so I have always had this message. However I am currently running Beryl and Emerald fine following the instructions here:
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)
The only exception is I had to use the svn repository for feisty at :
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy 
and
deb-src deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

(and you may want to set up startxgl as
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
sleep 4  
export DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

otherwise you lose the restart and shutdown buttons from the logoff options)

Edit: forgot to mention that you'll also have to specify beryl-manager separately in Synaptic.

---

