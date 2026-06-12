---
title: "VNC into dummy second monitor"
date: 2016-12-04
forum: Desktop Environments
---

### Post by PhilTroy on 2016-12-04
Hi!

I have two (actually more but that's irrelevant) Lubuntu 16..04 computers.  On my rightmost Lubuntu computer I have a single monitor and a 1920x1080 HDMI display.  To its left I have another Lubuntu computer with a 1920 x 1080 monitor.  I wish to be able to run a program (netbeans or eclipse) on the rightmost computer and the rightmost screen and to then detach one of the windows and move it so it is visible on the computer to the left.  I know that others have tried this (with varying degrees of success).  I got the following to work on the rightmost machine
[INDENT][B]xrandr --addmode VIRTUAL1 1680x1050

Using arandr ( I couldn't do this with xrandr) I moved the VIRTUAL1 display to the top left and HDMI1 immediately to its right

x11vnc -clip 1680x1050+0+0[/B][/INDENT]

On the machine to the left I ran xtightvncviewer, specified the correct tcpip address and port (192.168.0.112:5900), undecorated it, and used the the menu panel to start up netbeans.

There are a few things I got stuck on along the way and am still stuck on:

[I]- I would like the right monitor to be the primary monitor.  I tried with xrandr, and I tried with a custom xorg.conf (which I will post below).  
  I know that there are many posts about this - if anyone has found a solution I would appreciate being pointed to it

- x11vnc has the -clip option; I am wondering whether any other vncservers have anything similar.  (I think realvnc may but I would rather avoid paying for it on an annual basis)

- When I used any vnc viewer other than xtightvncviewer, after moving the mouse into the viewer and then out, I could not get the viewer to display the cursor again.
   I am wondering whether I am doing something wrong, or whether this is a bug in either xtightvncviewer, or all of the other vncviewers.

- I am wondering whether there is a significantly easier approach to doing this; in my naieve mind I thought that I should be able to easily add another x11 screen (or display)
  but from what I have read the program will only work in one x11 display at a time.  I tried using xorg.conf to create a dummy screen and to position but this never worked for me.
[/I]
Thanks . . .

Phil

The following conf file seemed to work in that it changed the display resolution to 1600x900 (which was my way of testing it)
[INDENT]**Section "Device"**[/INDENT]
[INDENT]**    Identifier  "HDMI1Device"**[/INDENT]
[INDENT]**    Driver "intel"**[/INDENT]
[INDENT]**EndSection**[/INDENT]
[INDENT]**Section "Monitor"**[/INDENT]
[INDENT]**    Identifier  "HDMI1"**[/INDENT]
[INDENT]**    Option      "PreferredMode" "1600x900"**[/INDENT]
[INDENT]**    Option      "Position" "0 0"**[/INDENT]
[INDENT]**    Option      "Primary" "true"**[/INDENT]
[INDENT]**EndSection**[/INDENT]
[INDENT]**Section "Screen"**[/INDENT]
[INDENT]**    Identifier  "RealScreen"**[/INDENT]
[INDENT]**    Monitor     "HDMI1"**[/INDENT]
[INDENT]**    Device        "HDMI1Device"**[/INDENT]
[INDENT]** EndSection**[/INDENT]

The following conf file did not seem to work:
[INDENT]**Section "Device"**[/INDENT]
[INDENT]**    Identifier  "DummyDevice"**[/INDENT]
[INDENT]**    Driver         "dummy"**[/INDENT]
[INDENT]**EndSection**[/INDENT]
[INDENT]**Section "Monitor"**[/INDENT]
[INDENT]**    Identifier  "VIRTUAL1"**[/INDENT]
[INDENT]**    Option      "PreferredMode" "1600x900"**[/INDENT]
[INDENT]**    Option      "Position" "1600 0"**[/INDENT]
[INDENT]**EndSection**[/INDENT]
[INDENT]**Section "Screen"**[/INDENT]
[INDENT]**    Identifier  "DummyScreen"**[/INDENT]
[INDENT]**    Device        "DummyDevice"**[/INDENT]
[INDENT]**    Monitor     "VIRTUAL1"**[/INDENT]
[INDENT]** EndSection**[/INDENT]
[INDENT]
[/INDENT]

---

### Post by TheFu on 2016-12-06
Have you tried using straight X11 to place the screen?  Inside the same LAN, this is easier than VNC-anything.
```

$ ssh -X userid@serverB program-to-be-run &
```

You can't move running programs between different X/displays. Not designed for that. The VNC idea isn't a bad one - if you run the tool inside VNC, then you can detach from that (it will go away) and re-connect from a different display or/and machine.

I find it is easier to have 1 machine control all the monitors and use remote **ssh -X** into any others when running X-client programs. That will setup the DISPLAY environment variable and use the ssh tunnel for all the X11 traffic to be returned to the X-server.  the remote sshd-config needs to allow X11 tunnels.
This might help: [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)

X11 is a client/server protocol.  The "server" is the physical machine we sit behind and the X-client runs on the remote system. There is a different X-server for each GPU and no way to move a client/server connection between a different client and/or different server.  Getting over that architecture limitation is what you want.  Perhaps there is an X11-proxy that can play middle-man for the client and/or the server retaining a connected state as the other side is moved?  X11 has pretty weenie security, but the ~/.Xauthority file is there.

A quick google turned up Xdmx.  Don't know anything about it, but it is really old.

---

