---
title: "VNC screen is grey"
date: 2006-09-22
forum: Desktop Environments
---

### Post by charles.g.moore on 2006-09-22
I followed one of the HOW-to's on this forum for setting up VNC server on my desktop, it seems the configuration went fine but when I fire it up to test it using 127.0.0.1 I can only get a grey (with pixel sized black dots) screen and no login screen

my terminal output looks like this:

charles@charles-desktop:~$ vncviewer localhost:1
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.8 (viewer 3.3)
Password:
VNC authentication succeeded
Desktop name "x11"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  16 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 31 green 63 blue 31, shift red 11 green 5 blue 0
Using default colormap and visual, TrueColor, depth 24.
Got 256 exact BGR233 colours out of 256
Using BGR233 pixel format:
  8 bits per pixel.
  True colour: max red 7 green 7 blue 3, shift red 0 green 3 blue 6

Could there be a problem with my dual monitor setup not translating well onto VNC?

---

### Post by beerorkid on 2006-09-22
you know I have tried VNC a few times and could never get it to work.

But I found something that does what I wanted anyway.

If you ssh into another linux box and pass the -X flag it will allow you to use X programs.

So: ```
ssh -X -l beerorkid 192.168.1.100 
```
(note that is a capitol "X"

so when you are in the ssh session enter whatever program you want to run aka konqueror, and it will show up on your screen.  very cool.

---

### Post by Sfac on 2006-09-22
What VNC server are you using? im using x11vnc and have no problems at all. check this excellent how to:
[http://www.ubuntuforums.org/showthread.php?p=236053](http://www.ubuntuforums.org/showthread.php?p=236053)

---

