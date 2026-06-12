---
title: "Leave GUI apps running remotely"
date: 2008-04-16
forum: Desktop Environments
---

### Post by tekguy on 2008-04-16
I have been trying to figure out how to leave GUI apps running on my 7.10 install when I remote into the box. I am using Pan Newsreader and I don't want it to close when I leave the box.

Right now what I have set up is XDMCP. I can remote into the box fine. But if I launch and app and then leave it closes. I have seen some people say to use VNC. But I can only get VNC to work if I attach a monitor to my linux box, log into the machine, at which point I can VNC into the box. I want to be able to VNC and log into the box without having to plug a monitor, keyboard, and mouse up to the machine.

Is VNC the way to go and I am just not doing something right? I would hate to have to hook that machine up to a monitor, keyboard, and mouse to log in just so I can then remote in.

---

### Post by trippinnik on 2008-04-17
I recommend ssh X forwarding.  It'll forward just the application you want to run.
You'll need to enable it in ssh's config.  On the server:
```
su nano /etc/ssh/sshd_config
```
then uncomment the line and make sure it says 'yes'
[CODEX11Forwarding yes[/CODE]
then on the client
```
ForwardAgent yes
ForwardX11 yes
```
make sure to restart sshd 
```
sudo /etc/init.d/sshd restart
```
then login to the ssh server and you can run GUI apps from the command line.

---

