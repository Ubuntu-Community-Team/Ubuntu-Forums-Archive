---
title: "Not able to start X application of remote machine ( via ssh ) on Ubuntu box"
date: 2005-09-08
forum: Desktop Environments
---

### Post by Prakash Prabhu on 2005-09-08
Hi,

I am a new user of Ubuntu. I opened an xterm on my Ubuntu
box and then sshed into a Debian machine ( Sarge ) and then 
tried to start an X application ( tried with eclipse, firefox ) :

my ubuntu$ ssh user@debian-mc
debian-mc$ firefox 

but it gave the following error :

xdpyinfo:  unable to open display "".
Unable to connect to X server

(firefox-bin:20442): Gtk-WARNING **: cannot open display:
firefox-bin exited with non-zero status (1)

However I am able to start the same application by sshing into the Debian
machine from other Debian machines ( instead of my Ubuntu machine ).

Thanks in advance for any help.

- Prakash

---

### Post by KingBahamut on 2005-09-08
I believe this is involved in X11 forwarding on the session. 

I believe this involves enabling XDMCP through ssh. 

Docs:
[http://www.tldp.org/HOWTO/XDMCP-HOWTO/ssh.html](http://www.tldp.org/HOWTO/XDMCP-HOWTO/ssh.html)

However do note that if someone on the server can read your /.Xauthority file (hopefully only root, but if you have bad file permissions you're in trouble), and can connect to the port that sshd has bound (which anyone can) then they can access your desktop's X11 server, even if they're not anywhere near you!

Let's reiterate: if you log in via SSH to a remote server with X11 forwarding, root on that server can access your desktop, sniff your keystrokes, abuse your windows, you name it. If you have bad permissions on your /.Xauthority file, then anyone on that server can control your desktop.

---

### Post by professor_chaos on 2005-09-08
But if you want to tunnel...

ssh -X username@host

    ```
 -X      Enables X11 forwarding.  This can also be specified on a per-host
             basis in a configuration file.

             X11 forwarding should be enabled with caution.  Users with the
             ability to bypass file permissions on the remote host (for the
             user’s X authorization database) can access the local X11 display
             through the forwarded connection.  An attacker may then be able
             to perform activities such as keystroke monitoring.

     -x      Disables X11 forwarding.

     -Y      Enables trusted X11 forwarding.
```

---

### Post by Prakash Prabhu on 2005-09-09
Thanks a lot guys ! It worked.

- Prakash

---

