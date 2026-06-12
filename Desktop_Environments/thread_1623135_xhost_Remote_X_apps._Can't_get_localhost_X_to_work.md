---
title: "xhost Remote X apps. Can't get localhost X to work"
date: 2010-11-16
forum: Desktop Environments
---

### Post by rickyrockrat on 2010-11-16
To get X apps to work remotely, (for instance, I have a 16500C logic analyzer that I can control from my Linux host, and it's *much* easier than using the touch screen).  I've gone through a lot of posts, but nobody seems to have the full picture.  Here's my attempt.

First, Are you trying to do startx remotely? If so, you are not trying to remote just one client, you are trying to run the X server, so likely what you want is
xtightvncviewer (local)
tightvncserver (remote)
And none of this tutorial applies to the above scenario. Briefly, install those two using apt-get on the respective machines, then on the remote, use vncserver. The first time it will ask for a password. This password will be used on the client. vncserver --help is pretty self-explanatory.  Then you just do vncviewer host, and type in the password previously set up on the remote box.
Now if you are *not* trying to run the whole desktop, and just want single applications, read on.


Assume the host we want to display remote X windows on is 192.168.0.20, and the remote host is 192.168.0.10.

You have to have 3 things working.
1) A network connection (ping to make sure it's there)
2) X needs to be listening
3) X needs to allow the host to connect.

1)
Going through these, make sure you can ping. Go to one of the machines and type: 
```
ping 192.168.0.10 
```
(or whatever the remote host IP is).

If you get a response, you've got an IP connection. If not, check your cables, check to see that your light is on (on the card or switch or hub), etc. 

2OPTION: With X running, type 
```
ps aux|grep X
```
See if there is any nolisten tcp on any of the lines, if there is, you get to find out where that is put.  The nolisten tells X to not listen to tcp connections, which is a good security feature.

2CHECK:
If there is not a nolisten, then try this:
```
telnet localhost 6000
```
You should see:
```
Connected to localhost.
```
Type Ctrl-]
then quit to leave the telnet session.
If you have this connection, then go to step SETXHOST (below).

If you see the nolisten, you've got to find who or what is putting that X server arg there.

The two places I checked and edited files are 
/etc/X11/xinit/xserverrc
And 
/etc/kde4/kdm/kdmrc
Presumably, you will find the Gnome config here
/etc/gdm/gdm.conf

FIRST, create a backup of these files:
```
sudo cp /etc/X11/xinit/xserverrc /etc/X11/xinit/xserverrc.orig
```
```
sudo cp /etc/kde4/kdm/kdmrc /etc/kde4/kdm/kdmrc.orig
```
```
sudo cp /etc/gdm/gdm.conf /etc/gdm/gdm.conf.orig
```

Please see this link on getting the gnome to work.
[http://ubuntuforums.org/showthread.php?p=10123474](http://ubuntuforums.org/showthread.php?p=10123474)

Then edit the files:
```
sudo vi /etc/X11/xinit/xserverrc
```
Find the line where the -nolisten tcp is, and put the cursor over the - and type x (delete char). Do this until the '-nolisten tcp' is gone. Then type ```
:wq
``` to write and quit.
Do this again for your log in daemon:
```
sudo vi /etc/kde4/kdm/kdmrc
```

Then log out of your X session, click the power button/menu on the login screen and select 'Restart X server'.
Got to 2OPTION, then 2CHECK.  Once 2CHECK is successful, set up the authentication, which is done with xhost.

SETXHOST

type 
```
xhost +localhost
```
then type 
```
export DISPLAY=localhost:0.0
```
then
```
xeyes
```
You should see a set of big Eyes show up. Hit Ctrl-C
type 
```
export DISPLAY=:0.0
```
to return the terminal to normal operation.

Now finally, you add whatever hosts you want to access the X server:
```
xhost +192.168.0.10
```

And go to the remote host (192.168.0.10) and see if you can connect.  Set your display on the remote like so:
```
export DISPLAY=192.168.0.20:0.0
```
Then try xeyes as before. Once you've got it all working, go grab yourself your favorite beverage and toast your success. And toast all the excellent open source developers that allowed this to happen.

You can always just do
```
xhost +
```
BUT you are allowing ANYBODY to connect (i.e. turning off authentication).  

You should go over ssh if you are on a non-trusted network (.i.e. you are at home behind a firewall).

Cheers!

---

