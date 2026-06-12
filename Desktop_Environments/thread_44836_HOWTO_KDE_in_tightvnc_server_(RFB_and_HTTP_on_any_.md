---
title: "HOWTO: KDE in tightvnc server (RFB and HTTP on any port)"
date: 2005-06-27
forum: Desktop Environments
---

### Post by connellr on 2005-06-27
After installing tightvnc server via apt-get:

launch the server once as the user you want to run the service as using the command *vncserver*.  Then set the password you want for the vnc session.

Next, stop the service with *vncserver -kill :1* 

Now change to your home vnc configuration directory:
*cd ~/.vnc/* 

Rename your xstartup file (just incase this doesn't work):
*mv xstartup xstartup.orig* 

Create xstartup file with the following text:
*gedit ~/.vnc/xstartup* 

```

#!/bin/sh

##xrdb $HOME/.Xresources
##xsetroot -solid grey
##x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
##x-window-manager &

##/etc/X11/xinit/xinitrc &
/usr/bin/startkde -geometry 80x24+10+10

``` 

Now when you start vncserver it will launch KDE.

------------------------------------------------------------------------------------------------

VNCSERVER STARTUP/SHUTDOWN SCRIPTS (configure any port you want too)...

Create a file called vnc (or whatever you want) in your home directory:
*gedit ~/vnc* 

```
tightvncserver -rfbport 1234 -httpport 1235
``` 
(change the port numbers to whatever ports you want to run on).

Now create a file to stop the service ... we'll call it vnc.stop
*gedit ~/vnc.stop* 

```
vncserver -kill :1
``` 

Lastly, make these 2 files executable:
*chmod 700 vnc* 
*chmod 700 vnc.stop* 

Thats it, any time you want to seart vncserver type ~/vnc
And when your done using it and want to stop it type ~/vnc.stop

** Side Note:  This assumes you will only run one vnc session at a time, if you plan to run multiple vnc sessions these scripts will need to be modified a little to change the window number. **

---

