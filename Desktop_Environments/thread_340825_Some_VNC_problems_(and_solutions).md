---
title: "Some VNC problems (and solutions)"
date: 2007-01-17
forum: Desktop Environments
---

### Post by abovett on 2007-01-17
I run several Ubuntu and Kubuntu boxes and I've been having some problems with VNC. I've found workarounds which I'm posting here in case others are having the same problems. I'd also be interested to know if anyone else can reproduce these problems as I am considering raising bug reports for them.

1. ALT key problem with vncviewer

On two of my Ubuntu Edgy (Gnome) boxes, I have a problem if I VNC into another PC using vncviewer and use the Alt key (note that the "Terminal Server Client" actually calls vncviewer for vnc connections). Once Alt has been pressed it behaves like it's held down continuously so for example "Alt-x x" behaves like "Alt-x Alt-x". The session then becomes unusable as I can find no way to release it.

Strangely this does not happen on two of my other Ubuntu boxes - one of which is another Edgy box and another a Dapper box. All PCs have the latest Ubuntu updates installed.

The workaround I found was to install xvnc4viewer and use that instead.

2. Krfb slow and unreliable

I have tried Krfb as a VNC server on two Kubuntu boxes. In both cases I found that a connection from a Ubuntu client running vncviewer or xvnc4viewer often failed as soon as it started. I tried three different clients - two running Edgy and one running Dapper - with the same result. The error message was usually "Rect too big", though other errors also occurred. If it did connect it was very sluggish.

Connecting using Krdc from another Kubuntu box seemed to be OK.

The workaround I found was to install x11vnc and use that as a server when connecting from a Ubuntu client. It seems much faster and does not cause the same errors.

So - anyone else confirm these problems or have any comments before i raise a bug report?

Cheers

Andy B

---

### Post by newruler on 2007-01-17
I've been using this command for the vnc server (both boxes on Ubuntu Edgy with Gnome as the Desktop.. all updates installed.. few external repositories...
"xvcviewer -forever -display :0 "

then from my other computer I connect via an encrypted SSH tunnel with a little Compression enabled...
"ssh server.ip.address -p fowardedport -o Compression=yes -o CompressionLevel=1 -L 5900:localhost:5900"

I don't have a live IP Address on my server box that I connect to.. I forward a port through my firewall...
That brings me to a logon promt via the ssh tunnel to my Server... I logon with my regular user/password for the  Server
next I run "vncviewer -fullscreen localhost:0" from the computer that I just created the ssh tunnel on... the -fullscreen is added in just to give me a full screen display instead of a windowed display.  This seems to work pretty darn good for me... Server is sits on a Charter High Speed Cable Connection at 3Mbps down by 1Mbps up...  I connect from Hotel high speed networks and it seems to work really good for me.. plus it is encrypted...

it's not really related to the bugs you seem to be seeing... but thought it worth sharing...

---

### Post by fakie_flip on 2007-06-05
How can I send an alt key to the server? The server is FC5 running on a PS3. The alt keeps getting sent to the local computer instead of the remote one.

---

### Post by bazzer on 2007-10-09
> **fakie_flip said:**
> How can I send an alt key to the server? The server is FC5 running on a PS3. The alt keeps getting sent to the local computer instead of the remote one.

+1 - anyone?:confused:

---

### Post by lankford on 2007-10-26
Press F8 for the menu, ctrl and alt are there

---

### Post by lankford on 2007-10-26
> **newruler said:**
> I've been using this command for the vnc server (both boxes on Ubuntu Edgy with Gnome as the Desktop.. all updates installed.. few external repositories...
"xvcviewer -forever -display :0 "

then from my other computer I connect via an encrypted SSH tunnel with a little Compression enabled...
"ssh server.ip.address -p fowardedport -o Compression=yes -o CompressionLevel=1 -L 5900:localhost:5900"

I don't have a live IP Address on my server box that I connect to.. I forward a port through my firewall...
That brings me to a logon promt via the ssh tunnel to my Server... I logon with my regular user/password for the  Server
next I run "vncviewer -fullscreen localhost:0" from the computer that I just created the ssh tunnel on... the -fullscreen is added in just to give me a full screen display instead of a windowed display.  This seems to work pretty darn good for me... Server is sits on a Charter High Speed Cable Connection at 3Mbps down by 1Mbps up...  I connect from Hotel high speed networks and it seems to work really good for me.. plus it is encrypted...

it's not really related to the bugs you seem to be seeing... but thought it worth sharing...

to quickly login to a remote system I do this (NO COMPRESSION THO)

vncviewer -via some_server_at_work_with_sshd_running some_box_inside_my_network

This is nice because I have all of my boxes named by employee first initial last name,

If they call me at home I just drop to a terminal and type

vncviewer -via work.mydomain.com jdoe

put in the password an I am done

---

