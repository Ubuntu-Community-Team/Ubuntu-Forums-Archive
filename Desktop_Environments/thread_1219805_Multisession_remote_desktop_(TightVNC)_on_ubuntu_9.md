---
title: "Multisession remote desktop (TightVNC) on ubuntu 9.04 Jaunty Jackalope"
date: 2009-07-22
forum: Desktop Environments
---

### Post by BioComputing on 2009-07-22
I found a working solution (this works 100 % on fresh instalation):

Ubuntu menu:
**"System"** -> **"Administration"** -> **"Login window"**
On **"Remote"** tab:
- choose: **"Same as local"**
- button: **"Configure XDMCP"** and **uncheck "honor indirect request"**


1.) install xinetd, tight vncserver & viewer:

```
sudo apt-get update

sudo apt-get install xinetd

sudo apt-get install tightvncserver

sudo apt-get install xtightvncviewer

```

------------------

2.) Start vncserver and enter vnc password:

```
sudo vncserver :1
```

------------------

3.) Stop vncserver:

```
sudo vncserver -kill :1
```

------------------

4.) Open GDM.conf in editor:

```
sudo gedit /etc/gdm/gdm.conf
```

...make sure these two lines in [XDMCP] section are uncommented and looks like this:


```
[XDMCP]


Enabled=true


Port=177


```

-------------------


5.) Open "/etc/services" in editor:


```
sudo gedit /etc/services
```


To add vnc to services list, add this line at the end of file:


```
vnc		5901/tcp			# Xvnc
```


-------------------


6.) To add vnc service to xinetd:


```
sudo gedit /etc/xinetd.d/vnc
```


...Add following lines:


```
# description: The vnc server provides remote desktop connections

#

service vnc

{

	disable = no

	socket_type = stream

	protocol = tcp

	wait = no

	user = nobody

	server = /usr/bin/Xvnc

	server_args = :1 -inetd -once -query localhost -depth 24 -geometry 1024x768 -ac

}
```


-------------------


7.) Reboot server:

```
sudo reboot
```


-------------------

At last! Remote desktop works! Try login from other computer with any VNC client (I'm using RealVNC VNC viewer free edition on MS Windows Vista) and you'l get GDM login screen. For example, if your ubuntu server is at 192.168.0.8 enter this into vnc viewer: 192.168.0.8:5901

---

### Post by Colypso on 2009-08-22
Thanks this works perfectly!

---

### Post by minhu314 on 2009-08-24
It is good!

But,the audio for multisession is still a problem.

There is no remote sound.

Any idea?

---

### Post by elegar on 2009-10-05
:( Sorry I take the error , $cat ~/.vnc/*log:


Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
05/10/09 09:51:37 Xvnc version TightVNC-1.3.9
05/10/09 09:51:37 Copyright (C) 2000-2007 TightVNC Group
05/10/09 09:51:37 Copyright (C) 1999 AT&T Laboratories Cambridge
05/10/09 09:51:37 All Rights Reserved.
05/10/09 09:51:37 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
05/10/09 09:51:37 Desktop name 'X' (desarrollo:1)
05/10/09 09:51:37 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
05/10/09 09:51:37 Listening for VNC connections on TCP port 5901
xrdb: No such file or directory
xrdb: can't open file '/root/.Xresources'
xsetroot:  unknown color "grey"

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log


* And in the remote client the vnc appears in grey.

---

