---
title: "Help with setting up VNC without gdm login screen"
date: 2009-03-01
forum: General Help
---

### Post by rdilliker on 2009-03-01
My goal is to setup a VNC server on my ubuntu desktop so that I can tunnel VNC over SSH from my windows desktop. Also, I want to see what's on my desktop as if I am sitting in front of the ubuntu machine as opposed to a GDM login screen. Basically, a windows remote desktop type of usage model.

I've followed the [HOWTO: Setup vncserver+gdm]("http://ubuntuforums.org/showthread.php?t=795036&highlight=vnc") tutorial and can tunnel VNC over SSH using putty from my windows machine but the only problem now is that I get a GDM login screen which I don't want. I have installed vnc4server and xinetd and read up a bit on both of those to figure out their config files but haven't been able to figure out what to change.

This is my xinetd service configuration (/etc/xinetd.d/Xvnc) for Xvnc:```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -$
        port = 5901
}

```
Any help would be greatly appreciated.

---

### Post by rdilliker on 2009-03-02
Bump.

---

### Post by rdilliker on 2009-03-02
Night crew?

---

### Post by rdilliker on 2009-03-04
Someone must know the answer to this. Unfortunately I am on a dead end and don't know what else to search for.

---

### Post by rdilliker on 2009-03-06
I'm sure this is simple for someone but I'm at a dead end trying to figure this out any further. Any help would be greatly appreciated!

---

