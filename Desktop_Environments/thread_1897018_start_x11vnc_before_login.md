---
title: "start x11vnc before login"
date: 2011-12-18
forum: Desktop Environments
---

### Post by kamaradski on 2011-12-18
Hi all,

Would like to setup a x11vnc service that starts BEFORE user login. I know there has been many simular threads here, however none of them are offering the correct solution for v11.10.

However i cannot seam to find the display manager startup script as described in the x11vnc documentation.

I will setup a SSH-tunnel to maintain security, in case you wonder.

Could anyone point me in the right direction ?

Cheers :)
kamaradski

---

### Post by kamaradski on 2011-12-20
Issue solved in the following alternative way that in my opinion is more neat then editing the display manager script:

[COLOR="Red"]**ATTENTION:**[/COLOR] In case you want to replicate this solution, please bear in mind the following:
- Having X11vnc sever always on, will consume always some resources.
- Having x11vnc always on, might impose a constant security risk to your system.
- Dont ever implement the below solution without SSL\TLS or SSH-tunnel
- Unlike me you might add a flag to force some sort of encryption to save bandwidth
- You probably want to change the port to something more obscure
- Please note x11vnc will run as root in the below setup


Create /etc/init script that uses upstart to run the script AFTER x-server has started. call it for instance x11vnc.conf.

```

start on login-session-start
script
x11vnc -bg -reopen -forever -display :0 -localhost -rfbport 5900 -auth /var/run/lightdm/root/:0 -o /var/log/x11vnc.log -rfbauth /location/toyourpasswordfile/passwd
end script

```

KR
kamaradski

---

### Post by dentaku65 on 2011-12-20
I suggest to create an init script
```
sudo cp /etc/init.d/skeleton /etc/init.d/vnc_x11
```
Configure the /etc/init.d/vnc_x11 properly for your app (x11vnc)
```
sudo leafpad /etc/init.d/vnc_x11
```
The part under PATH section:
> PATH=/sbin:/usr/sbin:/bin:/usr/bin
DESC="Description of the service"
NAME=daemonexecutablename
DAEMON=/usr/sbin/$NAME
DAEMON_ARGS="--options args"
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME
Then, apply the script to the System-V init
```
sudo update-rc.d vnc_x11 defaults
```
Reboot.

---

### Post by kamaradski on 2011-12-26
And what is the difference in your solution and the one posted by me ?

Any good reasons why i should switch ? (not contradicting, just curious)

KR
kamaradski

---

### Post by dentaku65 on 2011-12-26
> **kamaradski said:**
> And what is the difference in your solution and the one posted by me ?

Any good reasons why i should switch ? (not contradicting, just curious)

KR
kamaradski

AFAIK, the difference is that you can administer the System-V init script with *service* command

No need of passing something like
> /location/toyourpasswordfile/passwd

br,
den

---

### Post by irvin on 2012-02-11
This works great ! With all you probably need:

before login screen, secure, with password and numeric keys are working !

[http://www.dannratemal.de/?p=450](http://www.dannratemal.de/?p=450)

---

