---
title: "x11vnc xrdp 14.04 setup"
date: 2015-07-02
forum: Desktop Environments
---

### Post by haskell3 on 2015-07-02
I recently lost my ubuntu box to a flood and am now setting up a new 14.04 installation. While the old installation was never perfect, the x11vnc and xrdp installation did a few things I can not seem to recreate.

In the old set up whenever I logged in either by terminal or remote desktop from windows machine, a new vnc port would be assigned and I would get a window telling me my vnc port. 

In the present setup, a vnc port (or at least tcp port that vnc listens to) is set up for the terminal log in screen (set to 5900) and a port is created for the user once logged in (e.g. 5901 so 5900 and 5901 both are for the same session). The second port probably owes to having set x11vnc to run in the .profile (trying everything I can think of here).  When I connect with remote desktop from the windows machine no vnc port is made.  I would like to have vnc access to each log in for each user.  Just not sure how to set this up.

the current /etc/init.d/x11vnc.conf 
# description "Start x11vnc at boot"


description "x11vnc"


start on runlevel [2345]
stop on runlevel [^2345]


console log


respawn
respawn limit 20 5


#start on login-session-start


#script


exec /usr/bin/x11vnc -xkb -auth guess -forever -loop -noxdamage -repeat -rfbauth /home/vnc/.vnc/passwd -shared -bg -o /var/log/x11vnc.log


#end script


the ~/.xsession file just contains:
xfce4-session

any help appreciated. thank you in advance.

---

### Post by TheFu on 2015-07-03
Wow. That seems hard.  **x2go** is more secure and provides a great experience (feels about 2-3x faster than VNC/RDP).
Steps:
* get ssh working between the client and server in the normal way. ssh-keys for authentication, highly recommended.
* add the x2go PPA on the server-side, install the server - [http://wiki.x2go.org/doku.php/wiki:repositories:ubuntu](http://wiki.x2go.org/doku.php/wiki:repositories:ubuntu) 
* add the x2go PPA on the client-side (or download the OSX/Windows clients), install the client
* If you don't have xfce4 or lxde - install one of them (or another supported DE). x2go works best with a few DEs, not Unity.
* On the client-side, run the client and configure the connection.  If you setup ssh-keys, those make the connections seamless.
* If performance is not great, reduce the compression method for jpeg sizes. The defaults are a little high, IMHO.

General install steps: [http://wiki.x2go.org/doku.php/doc:installation:start](http://wiki.x2go.org/doku.php/doc:installation:start)

Everyone who has switched has been amazed at the performance. Plus it works the same way from anywhere in the world with just an ssh port open. I do reduce the compression when in Asia a little more to keep the same "desktop feel" of speed.

---

### Post by haskell3 on 2015-07-06
Thank you for the reply. I managed to stumble onto this post today which does exactly what I was looking to do:

[http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)

---

### Post by TheFu on 2015-07-06
I realize that you wanted vnc/rdp solutions, but if you try x2go, you'll never go back. Promise.

---

