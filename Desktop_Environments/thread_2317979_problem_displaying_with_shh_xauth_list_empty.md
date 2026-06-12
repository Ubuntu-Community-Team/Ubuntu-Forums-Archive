---
title: "problem displaying with shh: xauth list empty"
date: 2016-03-22
forum: Desktop Environments
---

### Post by rienkevin on 2016-03-22
Hello, I have a problem to display remotely from windows via ssh. I've try for hours now and I don't get where do the problem come from :


I tried:

First: 
```

ubuntu@server2:~$ xeyes&
[1] 26074
ubuntu@server:~$ Error: Can't open display:

```

Then:
```

ubuntu@server2:~$ export DISPLAY=:0.0
ubuntu@server2:~$ echo $DISPLAY
:0.0
ubuntu@server:~$ xeyes&
[1] 26912
ubuntu@server:~$ No protocol specified
Error: Can't open display: :0.0

```

checking: /etc/ssh/ssh_config
```

ForwardAgent yes
ForwardX11 yes
ForwardX11Trusted yes

```

checking: /etc/ssh/sshd_config for 
```

X11Forwarding yes
X11DisplayOffset 10
X11UseLocalHost no
UseLogin no

```

Also:
```

cd /home/machine
mv .Xauthority .Xauthority.old
touch .Xauthority
Chown ubuntu:ubuntu .Xauthority
*restar*
ubuntu@server:~$ xauth listubuntu@server:~$

```

And:
```

ubuntu@server:~$ sudo startx


_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running
(EE)
Fatal server error:
(EE) Cannot establish any listening sockets - Make sure an X server isn't already running(EE)
(EE)
Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE)
(EE) Server terminated with error (1). Closing log file.
Invalid MIT-MAGIC-COOKIE-1 keyxinit: giving up
xinit: unable to connect to X server: Interrupted system call
xinit: server error

```

Someone has an idea ?

Regards,

Ottis

---

### Post by steeldriver on 2016-03-22
Are you trying to display xeyes on the local (Windows) machine or the remote machine? Is the remote machine a true server (CLI only) or does it have a GUI?

BTW I don't recommend EVER using sudo to run startx - causes lots of problems with .Xauthority ownership

---

### Post by rienkevin on 2016-03-22
I try to display xeyes (or whatever leads to something on the screen) remotely. I have a server on linux and I want to display thing on my windows local machine

---

### Post by deadflowr on 2016-03-22
Are you running xming through putty?
Or trying something else?

---

### Post by rienkevin on 2016-03-22
I was trying by puTTy but that didn't work out, someone suggested me to use mobaXterm which is, I must say, really nice and easier to use.

One probleme I got is I can't even generate a xorg.conf, the command X - configure doesn't work for some reason..

Edit : and yes I check 'X11 forwarding' in the options when I login through mobaXterm

---

### Post by rienkevin on 2016-03-24
Okay ! The answer was :

1- Go to: /etc/ssh
2- Open sshd_config
3- Add the line: X11Uselocalhost no
4- Save and close
5- Restart ssh service: sudo service ssh restart
6- Login again, and start an application like xclock& or xeyes&

Here you go,

Bisous les copains

---

