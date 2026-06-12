---
title: "VNC not good enough"
date: 2006-12-16
forum: Desktop Environments
---

### Post by timmay on 2006-12-16
Ok so let my start by explaining what I want from VNC:-

[LIST=1]
[*]The ability to logon to same session as already running locally on my desktop
[*]Automatic lock screen when connection dropped ... must be presented with log in screen after disconnect!
[*]I do like the idea of a password to connect to the VNC server ... this can stay.
[*]More than 8bit colour using vnc4viewer in Ubuntu remotely with colour set to 24 bit (this works fine using tightvnc in Windows so I don't see why there is a problem here.)
[*]VNC is too bandwidth intensive compared to what Windows remote desktop is like is there a way of improving this without a high loss in quality and colour depth?
[/LIST]
I tried followed the instruction found [here]("https://help.ubuntu.com/community/VNC#head-77f3890451112de1f92fb9628503806e0441d963") but they didn't work so I followed some very similar however I can't remember where I found them.

The following setting I have used are saved in /etc/xinetd.d/Xvnc

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 24 -once -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/ -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5900
}

Thanks.

---

### Post by BlackHero on 2006-12-16
if the other computer have windows use remote desktop of windows =)

---

### Post by skirkpatrick on 2006-12-16
> **timmay said:**
> Ok so let my start by explaining what I want from VNC:-

[LIST=1]
[*]The ability to logon to same session as already running locally on my desktop
[*]More than 8bit colour using vnc4viewer in Ubuntu remotely with colour set to 24 bit (this works fine using tightvnc in Windows so I don't see why there is a problem here.)
[*]VNC is too bandwidth intensive compared to what Windows remote desktop is like is there a way of improving this without a high loss in quality and colour depth?
[/LIST]


Mine does that now.  When I VNC into my desktop, my remote desktop moves the mouse and manipulates the windows and I see that happen at the same time on the server.

The standard setup, which is what I use, shows me all 24-bits of color.

You might want to look into FreeNX.  It's much faster and there are clients for both Linux and Windows.  There are already threads in the forums as to how to set it up.

---

### Post by timmay on 2006-12-17
Ok thanks that looks better will give it a go when I have the time.

Can you confirm by login graphically it means it displays the normal login screen you see locally.

"if the other computer have windows use remote desktop of windows =)" 

I think you missunderstood. The server would be running Ubuntu 6.10 and the client would either be Windows or Linux of some for or another (usually Ubuntu).

---

### Post by Littleweseth on 2006-12-17
You may find XDCMP to be more interesting. It's inherently faster due to the way it works (telling a computer how to draw the windows it sees, as opposed to sending what is essentially a video stream) and feels almost like you're sitting in front of the other computer.

---

### Post by timmay on 2006-12-17
Ok that works on my LAN but when I enabled a redirect for UDP port 177 which is apparently the port for XDMCP it doesn't work.

I.E.
[list]
[*]Access is possible on 192.168.1.* range
[*]Access is not possible using my external IP. NAT loop back is enabled so I can access my web site using the domain, public IP and local sever name. I'd expect therefore to get access to XDMCP using my domain with a port forward on UDP 177.
[/list]
I'm using a Speedtouch 585 ADSL router if that helps.

There is still that same old problem. This like any other method I've tried still starts a new separate session and doesn't log me in to the session already running locally. This causes a few things to crash which is annoying. And I would have to start applications again that I already had open in the local session.

This is however looking to be a much better method and I'll therefore remove VNC.

One more thing I'd like to add is:- what about security? I read somewhere that the user name and password are not encrypted when sent over the net. Is this true and should I worry about this.

Oh and is there a Windows XP client for XDMCP? I'm really not to worried about this but I'd like the option.

Thanks

---

### Post by skirkpatrick on 2006-12-18
I've fooled around a little bit with FreeNX.  It's supposed to be much faster as well because it sends commands and not video streams.  Also, I believe it's completely encrypted.  And has both Windows and Linux clients.

---

