---
title: "Blank screen in vncviewer"
date: 2005-12-21
forum: General Help
---

### Post by george_apan on 2005-12-21
I have installed ubuntu breezy with xfce on an old desktop and would like to be able to use it remotely with vnc from my laptop running ubuntu with gnome. I have the two of them connected through a DSL modem/router and I can ping both ways. I have installed vncserver on the desktop and I have tsclient on my laptop.

When I run tsclient from my laptop I have selected VNC as protocol and have given 192.168.178.20:1 (that's my desktop's IP, somehow it does not recognize its name), I provide the password that is needed and all I get is an X blank screen where I cannot do absolutely anything. Now if I shut down the client I receive a message that says:

```
There was an error.

VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
Copyright blah blah
VNC server supports protocol version 3.3 (viewer 3.3)
VNC authentication succeded
Desktop name "george's X desktop (dimokritos:1)"
Connected to VNC server, using protocol version 3.3
VNC server default format:
32 bits per pixel
Least significant byte first in each pixel.
True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Warning: Cannot convert string "-*helvetica-bold-r-*-*-16-*-*-*-*-*-*-*" to type FontStruct
Using default colormap and visual, TrueColor, depth 24.
Got 256 exact BGR233 colours out of 256
Using BGR233 pixel format:
8 bits per pixel.
True colour: max red 7 green 7 blue 3, shift red 0 green 3 blue 6
```

Now I don't really know what all that is about. I've tried searching with google but came up with nothing useful. Any hints to make this work?

Oh, and when I'll get it to work I'm planning on having the desktop with no monitor so how would I make vncserver run each time it starts?

Thanks for any help.

---

### Post by gnu2tux on 2005-12-21
What happens if you use the plain old vncviewer tool rather than tsclient?

try experimenting with the vnc options given to you by vncviewer (eg vncviewer --help)

To get vncserver starting up with the machine, try this (as root, eg sudo bash):

create a textfile in /etc/init.d called vnc and put this in it:

```

#!/bin/bash
echo "* Starting VNC Server...."
vncserver &

then make a link to it in /etc/rc2.d:

ln -s /etc/init.d/vnc /etc/rc2.d/S20vnc

you will probably need a script that kills the vnc server too:

call it vnckill, again putting it in /etc/init.d

#!/bin/bash
echo "* Stopping VNC Server...."
vncserver -kill :1

```

the syntax of the vncserver -kill maybe wrong, as it's a while since i have used vncserver, so check it works before relying on it!

make a link to it in rc6.d (shutdown rc)

```

ln -s /etc/init.d/vnckill /etc/rc6.d/S20vnckill

make sure that you chmod the scripts so that they are executable:

chmod 755 /etc/init.d/vnc*

```

Hope this helps!

---

### Post by george_apan on 2005-12-21
Same thing if I use vncviewer. Seems like tsclient launches vncviewer anyway. I can't think of anything the available parameters have to do with my problem. It's the first time I try to use VNC so I don't have any experience in this. I took a look through the man pages as well but couldn't figure anything out. I'll try again tomorrow.

And thanks for the startup and shutdown scripts. They will be useful when I work this out... ;)

---

### Post by george_apan on 2005-12-22
Ok got it. I installed the rfb package on both machines and ran x0rfbserver on the desktop and xrfbviewer on the laptop and everything works. It seems that vncserver is not able to export display :0 but it opens another one where a window manager has to be loaded all over again and we don't want that.. ;)

---

### Post by gnu2tux on 2005-12-22
[QUOTE=george_apan]Ok got it. I installed the rfb package on both machines and ran x0rfbserver on the desktop and xrfbviewer on the laptop and everything works. It seems that vncserver is not able to export display :0 but it opens another one where a window manager has to be loaded all over again and we don't want that.. ;)[/QUOTE]


In that case, install the package called x11vnc - which exports the current display, not a new one..

---

### Post by george_apan on 2005-12-22
Yes that works too and it feels faster than rfb. Thanks a lot! :)

---

