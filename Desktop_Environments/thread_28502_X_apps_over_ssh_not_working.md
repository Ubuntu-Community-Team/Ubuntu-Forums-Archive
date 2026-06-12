---
title: "X apps over ssh not working"
date: 2005-04-20
forum: Desktop Environments
---

### Post by 8086 on 2005-04-20
EDIT: I have fixed this. Look at my latest posting in this thread
--------------------------------------------------------------------------------------------------

I looked through some posts, but none seem to answer my question:
Until recently I have been running Slackware both on my laptop and my desktop/server computer, running apps on the laptop over a ssh-tunnel. Now I installed Ubuntu on the laptop, and "of course" this does not work anymore  ](*,)  I thought it might have something to do with Firestarter blocking out the connection (it was so with NFS), but after disabling it, and making sure there were no iptables rules blocking, it still does not work! Why?

This is what I do:
user@laptop:ssh username@server
(... logged into server)
username@server$ xclock
Error: Can't open display: laptop:0

In .bash_profile on the server I have set DISPLAY=laptop:0, something which has always worked. What I'm wondering is that Xorg is configured by UBUNTU not to open port 6000? I though of this because of this output from nmap:

(The 5998 ports scanned but not shown below are in state: closed)
PORT    STATE SERVICE
22/tcp  open  ssh
111/tcp open  rpcbind
729/tcp open  netviewdm1

See? Nothing running on port 6000 where Xorg should have (normally) been. I guess the sshd server doesn't understand where it should connect to. Can someone help me *open up* my X-server so I can run apps remotely?

By the way. I know you are not supposed to have to set $DISPLAY, if sshd is set up to forward X, or if you run ssh with the "-X" option, but I have never got this to work.

---

### Post by ebrowne on 2005-04-20
Hey,
I as haveing a similar problem have been use to setting DISPLAT and xhost in the past.  I can't remember exactly what I changed but there is a setting in gdm that you need to change to allow remote X sessions to open on your display.  I also had to use ssh -x user@server but  I also did a ssh -v -x user@server and found that I had a permission problem on the server side once I fixed that I was ok.  I'll be on later tonight if you still have this problem I'll post the change I made to gdm but I believe I found the post in this fourm.

---

### Post by hokim on 2005-04-20
You have to enable "ForwardX11" in /etc/ssh/ssh_config

---

### Post by 8086 on 2005-04-20
> **hokim]You have to enable "ForwardX11" in /etc/ssh/ssh_config[/QUOTE]

As I suspected, this does not do anything. "ForwardX11 on" is the same as specifying "ssh -X" on the commandline. This is probably not where the problem lies.

I get this when I log into my server using ssh -X server_name:

Warning: No xauth data said:**
> 
Notably the default configuration of Debian GNU/Linux is to disable the X server listening on the TCP port. If you wish to use remote X on a Debian system, you should re-enable this by altering the way the X server is started. Look at /etc/X11/xinit/xserverrc for a start.

In this file you can see 
```

#!/bin/sh
exec /usr/bin/X11/X -dpi 100 -nolisten tcp
 
```

I'm gonna see what removing the -nolisten tcp option does, probably the X-server will be visible as an open port 6000, and then trying. I'll get back to you...

---

### Post by ssam on 2005-04-20
have you tried the command

xhost +

on the machine running the x server?

(note, this open up your server to any external clients, you have to read the man page to make it finer grained.)

---

### Post by 8086 on 2005-04-20
Yup, that's pretty much the first thing I did... I also tried the finer grained version xhost +server

EDIT:
I don't know why, but removing the -nolisten option (see post above)  did nothing towards opening any tcp-ports...

This is what I get when I use the verbose option in ssh -Xv server /usr/X11/xcalc

debug1: Sending environment.
debug1: Sending env LANG = no_NO.UTF-8
debug1: Sending command: /usr/X11/bin/xcalc
Error: Can't open display:

Why does not ssh send/set up the DISPLAY variable?

---

### Post by ebrowne on 2005-04-20
Hey,
Ok I had to change the line in /etc/gdm/gdm.com from
DisallowTCP=true

to 

DisallowTCP=false

restart gdm

Then on my server I also had a problem with permissions such that it could not create .Xauthority in the remote machine.  Once I changed that and issued 
ssh -X user@host  I can open any X window I want on my local box from that host.

The only way I could find the problem was to run ssh -Xv user@host I no longer need to run xhost +host or set my DISPLAY on the other host to be my localmachine.  

Hope this helps.

---

### Post by 8086 on 2005-04-21
[QUOTE=ebrowne]Hey,
Ok I had to change the line in /etc/gdm/gdm.com from
DisallowTCP=true
to 
DisallowTCP=false
restart gdm
[/QUOTE]

After running Slackware for years I'm not used to "things being done under the covers" such as gdm hindring Xorg from doing what Xorg is told in its config file. But your tip proved off! I ran gdmconfig and unhooked the option that said "always refuse tcp connections". After restarting gdm I could run apps remotely, but still not with auto-forwarding of my X connection. But this is where your second tip comes in:

[QUOTE=ebrowne]
Then on my server I also had a problem with permissions such that it could not create .Xauthority in the remote machine.  Once I changed that and issued 
ssh -X user@host  I can open any X window I want on my local box from that host.
[/QUOTE]

What option in the world could that be? I checked through /etc/ssh/sshd_config on the server, and yes, there were an option that was commented out:
# X11Forwarding no
In the manual page for sshd_config it says this:
[QUOTE=sshd_config]
X11Forwarding
             Specifies whether X11 forwarding is permitted.  The argument must
             be “yes” or “no”.  The default is “no”.

             When X11 forwarding is enabled, there may be additional exposure
             to the server and to client displays if the sshd proxy display is
             configured to listen on the wildcard address (see X11UseLocalhost
             below), however this is not the default.  Additionally, the
             authentication spoofing and authentication data verification and
             substitution occur on the client side.  The security risk of
             using X11 forwarding is that the client’s X11 display server may
             be exposed to attack when the ssh client requests forwarding (see
             the warnings for ForwardX11 in ssh_config(5)).  A system adminis&#8208;
             trator may have a stance in which they want to protect clients
             that may expose themselves to attack by unwittingly requesting
             X11 forwarding, which can warrant a “no” setting.
[/QUOTE]

I'd always though this was just the server equivelant of -X swich for the client, but it seems I have been wrong about that...

I changed this to 
X11Forwarding yes
and the next time I tested, everything worked!

Here is my output from running a command so that people can check what *should be* at the end of a verbose output.

$ ssh -Xv 192.168.0.1 'export DISPLAY=laptop:0;grip'

----- lots of output----
---this comes in the end after changing sshd_config---
debug1: Sending command: grip
/usr/X11R6/bin/xauth:  creating new authority file /home/XXX/.Xauthority
debug1: client_input_channel_open: ctype x11 rchan 3 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 4322
debug1: channel 1: new [x11]
debug1: confirm x11

---

### Post by rgarver on 2005-05-26
I found that xauth was not in the normal path.  I fixed it with:

> sudo rm -r /usr/bin/X11
> sudo ln -s /usr/X11R6/bin /usr/bin/X11

This fixed it for me.

---

