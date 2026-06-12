---
title: "Enable Shared Desktop From CLI?"
date: 2006-06-22
forum: Desktop Environments
---

### Post by FoggyMtn on 2006-06-22
Hey ya'll

Long story short, when my computer (linux dapper) boots, it automatically starts a gnome session.  But, before I can access it remtoely, I need to manually enable Desktop sharing (remote desktop) from the dropdown menu in gnome (system>prefs>remote desktop).  That's great until my computer reboots (like after an outage) and I'm no there to start the sharing...

Now, I'm out of town.  I can only log into my box via ssh.  I can't get a vnc connection going to localhost:0 like I normally can.  I tried starting vncserver:6 (or any number), but I can't connect that way either.

How can I enable Desktop Sharing (w/ or w/o a password) from the command line?

Thanks!!

Rob

---

### Post by phowardcom on 2006-08-24
I have exactly the same problem. I recently did a reinstall and forgot to enable the Desktop Sharing. Now I am at work and can SSH into the box but can't VNC to it.

Anyone got any ideas?

Cheers

Paul.

---

### Post by z_pod on 2006-08-24
Not for the the whole desktop but if you need to forward the gui of your remote apps (à la Metaframe), what about a nice ssh -X <user@whatever> ?

---

### Post by mssever on 2006-08-24
Two things I do: first, I've aliased ssh as follows:
```
alias ssh='ssh -o ForwardX11=yes'
``` Now, when I'm using another Linux box (or Windows with Cygwin/X), I can  start up a graphical program via the command line, just like I was sitting at the machine.

When it comes to vncserver, I'd set that up manually, like so (all this is on the server):[LIST=1]
[*]make sure that xinetd and vnc-common are installed.
[*]Create the VNC file: ```
sudo nano /etc/xinetd.d/Xvnc
```
[*]Paste the following into the file: ```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 800x600 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}
``` Change the geometry flag in the server_args to whatever display resolution you want.
[*]Run ```
sudo vncpaswd /root/.vncpasswd
``` and assign a password.
[*]Do ```
sudo /etc/init.d/xinetd restart
``` Your server should be up and running now, and should start automatically on boot.
[*]On your client machine, you should now be able to do vncviewer yourserver:1 (I always have to use :1).
[*]Hint: if you also have an ssh server on your server, you can increase your security by tunnelling vnc through ssh thus: ```
vncviewer -via your.server your.server:1
```[/LIST]

---

### Post by Jose Catre-Vandis on 2006-08-28
The command you need, for Gnome, is
```
vino-preferences
```
but you will need to ssh -X

---

### Post by kotnik on 2006-08-28
Also consider x11vnc program. I use it for quick GUI fixes. The most important thing, it will let you use current X running, just follow this steps:

```
ssh user@some.machine
export DISPLAY=:0.0
x11vnc
```

This will allow you to use running X just once and without password. Check x11vnc man page for more info.

---

### Post by motin on 2006-10-08
There is a HOWTO on this matter here:

HOWTO: Control the gnome VNC vino-server from the command line - [http://ubuntuforums.org/showthread.php?p=1592684](http://ubuntuforums.org/showthread.php?p=1592684)

Appropriate guides could also be:

HOWTO: Set up VNC server with resumable sessions (already done in this thread mostly) - [http://ubuntuforums.org/showthread.php?t=191564](http://ubuntuforums.org/showthread.php?t=191564)

OR 

HOWTO: FreeNX on Dapper LTS 6.06 - [http://ubuntuforums.org/showthread.php?t=241651&highlight=freenx+howto](http://ubuntuforums.org/showthread.php?t=241651&highlight=freenx+howto)

FreeNX is faster than VNC.

---

