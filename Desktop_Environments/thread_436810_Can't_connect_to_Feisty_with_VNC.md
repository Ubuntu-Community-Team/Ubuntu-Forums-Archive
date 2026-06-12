---
title: "Can't connect to Feisty with VNC"
date: 2007-05-08
forum: Desktop Environments
---

### Post by Azyx on 2007-05-08
I I can't connect to Feisty with vnc (vncviewer 192.168.1.4:0 ) or TSclient to a Ubuntu 7.04-machine, but have no problem to do the same to a Ubuntu 6.04 machine.

When i run vncviewer 192.168.1.4:0 I get this message:

azyx@black:~$ vncviewer 192.168.1.4:0
VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.7 (viewer 3.3)
Password: 
ReadFromRFBServer: rdr::EndOfStream
azyx@black:~$ 

I also have problem to connect to OS-X. 

With this message:

azyx@black:~$ vncviewer 192.168.1.5:0
VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.889 (viewer 3.3)
Password: 
VNC authentication succeeded
Desktop name "imac.local"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  32 bits per pixel.
  Most significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Using default colormap and visual, TrueColor, depth 24.
Got 256 exact BGR233 colours out of 256
Using BGR233 pixel format:
  8 bits per pixel.
  True colour: max red 7 green 7 blue 3, shift red 0 green 3 blue 6
Using shared memory PutImage
Throughput 20000 kbit/s - changing to Hextile
Throughput 20000 kbit/s - changing from 8bit
Using viewer's native pixel format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Unknown message type 255 from VNC server
ShmCleanup called
azyx@black:~$

I have tried to change to xtightvnc. Then i get an connection, but a black screen. Could move the mouse and make inputs with the keyboard.

/azyx

---

### Post by Azyx on 2007-05-12
Seems that i need to downgrade to Dapper :(

---

