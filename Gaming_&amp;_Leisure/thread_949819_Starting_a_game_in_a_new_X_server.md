---
title: "Starting a game in a new X server"
date: 2008-10-16
forum: Gaming &amp; Leisure
---

### Post by Tom--d on 2008-10-16
Hello,

I would like to start my games in a new X server because I'm running Compiz and opengl windows and fullscreen crash after around 10 mins of game play. I know why. Its due to the limitation in the intel driver and/or limitation in DRI.

I just want to start a game in a new server which I can access through CTRL+ALT+F8 and CTRL+ALT+F7 to get to my desktop.


So far, I have made a script to set it up but so far, im unsuccessful.
Here it is,
```
#!/bin/bash
DISPLAY=:1.0

xinit /usr/bin/darkplaces-glx $* -- :1.0

```

It launches the new X server with the X cursor and thats it.
In the terminal in my other X Server, it leaves this:
```
AUDIT: Thu Oct 16 20:06:12 2008: 2924 X: client 1 rejected from local host (uid 1000)
No protocol specified
..

```
Over and over again.

Could someone please help me :)


PS: Darkplaces is for quake one. Gotta love it when its all kitted up (new graphics etc, :D:D)

THANKS,
Tom

---

