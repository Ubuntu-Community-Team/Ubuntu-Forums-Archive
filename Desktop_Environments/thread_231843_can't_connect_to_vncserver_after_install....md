---
title: "can't connect to vncserver after install..."
date: 2006-08-07
forum: Desktop Environments
---

### Post by Mia_tech on 2006-08-07
hey guys.
I just installed vncserver on ubuntu server Dapper Drake, and started it with 
$vncserver
$vncpasswd
and everything went just fine, but I can't connect to the server from xp, checked connetiviy is ok...ping both ways, but when I ran nmap on server is not showing port 5900, which leads me to belive that is not accepting connection because port is not open.

any suggestions
thanks

---

### Post by cantormath on 2006-08-07
> **Mia_tech said:**
> hey guys.
I just installed vncserver on ubuntu server Dapper Drake, and started it with 
$vncserver
$vncpasswd
and everything went just fine, but I can't connect to the server from xp, checked connetiviy is ok...ping both ways, but when I ran nmap on server is not showing port 5900, which leads me to belive that is not accepting connection because port is not open.

any suggestions
thanks

try
vncserver -geometry 1024x768 -depth 16 

here is a tutorial for futher config...
[http://www.skullbox.net/vncserver.php](http://www.skullbox.net/vncserver.php)
Here is another one
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

---

### Post by scxtt on 2006-08-07
vncserver uses port 5901 ...

---

### Post by Mia_tech on 2006-08-07
I have installed "xubuntu-desktop" on server, and nmap didn't show either 5900 or 5901...

---

### Post by Mia_tech on 2006-08-07
> **cantormath said:**
> try
vncserver -geometry 1024x768 -depth 16 -color 16

here is a tutorial for futher config...
[http://www.skullbox.net/vncserver.php](http://www.skullbox.net/vncserver.php)

I have "xubuntu-desktop" installed

---

### Post by Mia_tech on 2006-08-07
> **scxtt said:**
> vncserver uses port 5901 ...

not running either

---

### Post by scxtt on 2006-08-07
how exactly are you trying to connect from XP? -- i use the viewer from RealVNC ... enter the IP address of the box i want to connect to, generally of the form 192.168.1.100:1 (you have to specify the :1 [or :2, :3, depends on how many vnc sessions you have running]) ...

and make sure vncserver is listed in a **ps -ef | grep vnc** which will also show you that it's using port 5901 --> (-rfbport 5901)

---

### Post by Mia_tech on 2006-08-07
how you get the service started I know in redhat is 
service vncserver start

how to do that with ubuntu?

---

### Post by scxtt on 2006-08-07
a simple **vncserver** will work, using default options ... i use:

vncserver -geometry 1600x1200 -depth 24

---

### Post by howlingmadhowie on 2006-08-08
have you checked things like proxy settings? though i'm not aware of proxies which would play around with the 590x ports,

---

### Post by Mia_tech on 2006-08-08
what's the iptable command to open port 5900, just to make sure is not rejecting connection, cause scanning the server from the network, is not reporting any 59XX port open.

---

### Post by Mia_tech on 2006-08-08
> **scxtt said:**
> how exactly are you trying to connect from XP? -- i use the viewer from RealVNC ... enter the IP address of the box i want to connect to, generally of the form 192.168.1.100:1 (you have to specify the :1 [or :2, :3, depends on how many vnc sessions you have running]) ...

and make sure vncserver is listed in a **ps -ef | grep vnc** which will also show you that it's using port 5901 --> (-rfbport 5901)

I did ran that command and this is the output

username 7172 5541 0 18:57 pts/0  00:00:00 grep vnc

:0(

---

### Post by scxtt on 2006-08-08
did you start a server from the terminal?

$:> vncserver -geometry 1024x768 -depth 24

for example, then try a **ps -ef | grep vnc**?

if it's not running, you'll NEVER be able to connect to it - open port issues or not ...

---

### Post by Mia_tech on 2006-08-08
> **scxtt said:**
> did you start a server from the terminal?

$:> vncserver -geometry 1024x768 -depth 24

for example, then try a **ps -ef | grep vnc**?

if it's not running, you'll NEVER be able to connect to it - open port issues or not ...

I did
> sudo vncserver -geometry 1024x768 -depth 24
and got this...
>New 'servername:1 (root)' desktop is servername:1
>Starting applications specified in /home/username/.vnc/xstartup
>Log file is /home/username/.vnc/servername:1.log

still troubleshooting......I noticed that in my .vnc folder there's no xstartup file

any ideas will be appretiated

---

### Post by Mia_tech on 2006-08-08
> **Mia_tech said:**
> I did
> sudo vncserver -geometry 1024x768 -depth 24
and got this...
>New 'servername:1 (root)' desktop is servername:1
>Starting applications specified in /home/username/.vnc/xstartup
>Log file is /home/username/.vnc/servername:1.log

still troubleshooting......I noticed that in my .vnc folder there's no xstartup file

any ideas will be appretiated

My mistake there is a xstartup folder

---

### Post by scxtt on 2006-08-08
why are you using sudo?

---

### Post by Mia_tech on 2006-08-08
> **scxtt said:**
> why are you using sudo?

yes and I tried from root and the resulst are the same, don't get any error yet still not running this is the output I get running from root.

>vncserver -geometry 1024x768 -depth 24
>New 'servername:1 (root)' desktop is servername:1
>Starting applications specified in /root/.vnc/xstartup
>Log file is /root/.vnc/servername:1.log

ran---> ps -ef | grep vnc
>root  5579  5191  0  23:17  pts/0   00:00:00 grep vnc

---

### Post by scxtt on 2006-08-08
no, i'm wondering why you're using sudo @ all - run vncserver as a regular user ...

---

### Post by Mia_tech on 2006-08-09
> **scxtt said:**
> no, i'm wondering why you're using sudo @ all - run vncserver as a regular user ...

did that too

---

### Post by scxtt on 2006-08-09
have you looked at **$USER/.vnc/servername:1.log** to see if there's an error in the log?

(seriously, getting VNC going isn't generally this hard ...)

---

### Post by Mia_tech on 2006-08-09
> **Mia_tech said:**
> did that too

I have done pretty much anything that comes to mind plus done some google around, but still can't get the service running, Im thinking  on posting the xservername.log file.....think that's the name not looking at it right now.

---

### Post by Mia_tech on 2006-08-10
> **scxtt said:**
> have you looked at **$USER/.vnc/servername:1.log** to see if there's an error in the log?

(seriously, getting VNC going isn't generally this hard ...)

I know usually, you have the system menu and enable remote desktop, but this was a server install with no GUI, and I choose to install xubuntu-desktop, after enabaling all the repositories, then again it might have not installed all components the, or it might be missing something, I have done updates and upgrade on it serveral times, but still can't run vncserver, I was thing on removing xubuntu-desktop and installing ubuntu-desktop, so I can enable vnc from the GUI.

---

### Post by Mia_tech on 2006-08-10
> **scxtt said:**
> have you looked at **$USER/.vnc/servername:1.log** to see if there's an error in the log?

(seriously, getting VNC going isn't generally this hard ...)

here is the xstartup file
===================================================================
#!/bin/sh

[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 1024x768+10+10 -ls -title "$VNCDESKTOP Desktop" &
twm &
==================================================================
"and this is the /ubuntu:1.log"
==================================================================

Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'

Xvnc Free Edition 4.1.2 - built May 12 2006 17:42:24
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 40201000, The XFree86 Project, Inc


Thu Aug 10 21:33:21 2006
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      Listening for HTTP connections on port 5801
 vncext:      created VNC server for screen 0
error opening security policy file /usr/X11R6/lib/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!

Fatal server error:
could not open default font 'fixed'
xsetroot:  unable to open display 'ubuntu:1'
/home/jorge/.vnc/xstartup: line 7: twm: command not found
vncconfig: unable to open display "ubuntu:1"
xterm Xt error: Can't open display: ubuntu:1

---

### Post by computergroove on 2006-08-10
You might try a differnet flavor of VNC like tightvnc or ultravnc. 

> /home/jorge/.vnc/xstartup: line 7: twm: command not found

sounds like a program error that was overlooked by the developer of the software. Try a older version or try a different flavor of remote viewer. Post your results with tight vnc.

---

### Post by scxtt on 2006-08-10
i think the problem here is SOLELY that you took the server version and stuck (some) GUI components on top of it ...

using tight or ultra isn't going to solve it either (at least i don't see how) ...

your best bet will be to do a non-server install ...

computergroove -- twm is a basic window manager, which probably isn't installed on that box either, so that error isn't a problem w/ VNC ...

---

