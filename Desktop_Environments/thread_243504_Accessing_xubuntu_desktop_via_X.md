---
title: "Accessing xubuntu desktop via X"
date: 2006-08-25
forum: Desktop Environments
---

### Post by phuoq on 2006-08-25
Hi,

I've just installed xubuntu 6.06 and I'm trying to access the desktop via X from a remote machine.

The IP address of the xubuntu box is 192.168.0.3 
The IP address of the remote machine is 192.168.0.1
On the local machine I type

local:~ $ xhost +

On the remote machine I type

remote:~ $ export DISPLAY=192.168.0.3:0.0

then

remote:~$ xeyes
Error: Can't open display: 192.168.0.3:0.0

I can ping the machine (network is fine). On the local machine I also tried a connection

local:~ $ export DISPLAY=192.168.0.3:0.0
local:~$ xeyes
Error: Can't open display: 192.168.0.3:0.0

But this does not work, I also tried on the loopback interface

local:~ $ export DISPLAY=localhost:0.0
local:~$ xeyes
Error: Can't open display: localhost:0.0

I read somewhere that by default debian does not listen for X tcp connections so I edited 

/etc/X11/xinit/xserverrc

And removed the -nolisten tcp option and restarted but this did not work. Can anyone help me configuring X/XFCE to accept incoming XDMP traffic over TCP.

Thanks.

PS I'm aware of the security implications with opening up X but this is a private network with just these two computers attached.

---

### Post by dmwit on 2006-08-25
You are aware of the security problem -- but are you aware of the secure solution?  It doesn't even require you to set any environment variables on the remote machine.  To wit, install the ssh daemon on the local machine, and on the remote machine, use
```
ssh -X 192.168.0.3
```
~d

---

### Post by phuoq on 2006-08-25
Thanks for this reply, I'm aware of ssh -X (I don't need it since all tcp ports are open between the two machines). 
The problem is that xfce is not listening for tcp traffic (using DISPLAY=192.168.0.3:0.0 on the machine running xfce did not work, only DISPLAY=:0.0). So even though the X11 traffic is forwarded by the tunnel there is nothing there to receive it.

I've also tried changing the xfce session config by commenting out DisableTcp=True in /etc/xdg/xfce4-session/xfce4-session.rc but there is still nothing listening on the correct port range (which I think is 6000-6063, correct me if I'm wrong).

Any other thoughts? 

Thanks.

---

### Post by phuoq on 2006-08-25
I found the answer, I needed to change the gdm conf to set DisableTCP to false.

---

