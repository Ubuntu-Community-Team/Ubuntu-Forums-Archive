---
title: "Remote X application usage problem"
date: 2005-01-31
forum: Desktop Environments
---

### Post by rlw on 2005-01-31
I'd like to use ubuntu to work remotely on our HP-UX servers. Unfortunately I cannot open any remote X applications, e.g if I try to launch an xterm on a HP-UX server, I allways get the following error message: 
Error: Can't open display: <my hostname>
Error: Couldn't find per display information.

I did xhosts+ on the local machine. I exported the display on the remote server to my machine, e.g. DISPLAY=name:0.0. I was checking the hosts.allow¦deny nothing unusal there. I worked that way all the time now, fo rsome reason it doesn't work with ubuntu.
I installed warty, use gnome and made updates using apt-get upgrade . 
Any ideas? Thanks!

---

### Post by mendicant on 2005-01-31
The default X server config won't listen for socket connections.  Typically, you would use ssh to tunnel the connection for you:

% ssh -X me@somewhere
.
.
.
# xterm &

As long as the remote ssh server allows the X connection, this should now pop up an xterm on your machine, but which is on the remote server.  You can also reenable listening to TCP connections, but you should prefer using SSH.

---

### Post by piedamaro on 2005-01-31
IIRC ubuntu has ForwardX11 no by default in /etc/ssh/ssh_config

---

### Post by mendicant on 2005-01-31
That's why I've got the -X option in the ssh command.  Actually, I suppose if you just wanted to bring up a terminal, you would do something like:

% ssh -Xfn me@somewhere xterm

---

### Post by rlw on 2005-02-01
Thanks for all your help :-) The thing is that we do not run sshd on our servers and have to use rsh tools (that's out of my influence   :(   I was checking for an equal option in rlogin, but couldn't find any.  BTW: I installed the rsh-client package in order to have rlogin available.
Can I allow X forwarding any other way?

---

### Post by rlw on 2005-02-01
Found the solution on: [https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=132629](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=132629)

Edit the /etc/x11/gdm/gdm.conf file and set DisallowTCP=true

 :D

---

### Post by mendicant on 2005-02-01
Yeah, this is the method I alluded to earlier.  As that redhat post implies, it's a bad idea in general, unless you're sure you're on a secure network.

---

