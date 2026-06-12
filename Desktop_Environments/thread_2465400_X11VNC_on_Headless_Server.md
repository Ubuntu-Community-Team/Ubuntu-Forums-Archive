---
title: "X11VNC on Headless Server"
date: 2021-07-31
forum: Desktop Environments
---

### Post by stephenstark on 2021-07-31
I am attempting to start x11vnc server on an Ubuntu 16.04 LTS headless machine.  I am issuing the following command via an SSH session:

**$ sudo x11vnc -create -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth guess -rfbauth /home/xxxxx/.vnc/passwd -rfbport 5900**

However, I am getting the following errors when attempting to start x11vnc:

[B]sudo: unable to resolve host hostname-domain-com: Connection refused
31/07/2021 18:55:51 passing arg to libvncserver: -rfbauth
31/07/2021 18:55:51 passing arg to libvncserver: /home/xxxxx/.vnc/passwd
31/07/2021 18:55:51 passing arg to libvncserver: -rfbport
31/07/2021 18:55:51 passing arg to libvncserver: 5900
31/07/2021 18:55:51 x11vnc version: 0.9.13 lastmod: 2011-08-10  pid: 23668
31/07/2021 18:55:51 -auth guess: failed for display=':0'
31/07/2021 18:55:51 -auth guess: since we are root, retrying with FD_XDM=1
31/07/2021 18:55:51 -auth guess: failed for display=':0'[/B]

I'm certain I am missing something - has anyone launched x11vnc on a headless server in a similar fashion before, and can offer guidance on how to overcome these errors?

Thanks in advance for the help!

---

### Post by TheFu on 2021-07-31
Support for 16.04 ended last April.

Would you consider using a better, faster, more secure answer that is 100% F/LOSS?  I use headless connections all.the.time. with x2go.  The systems don't have any GPU connected.

x11vnc is like telnet. Should have died off long, long, ago.
What's possible using different remote GUI access methods: [https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)

---

### Post by ActionParsnip on 2021-08-01
What is the purpose of the VNC connection? What activities will you be doing once you get connected to the desktop session? There may be a sleeker solution to what you want to do.

---

### Post by stephenstark on 2021-08-01
Thank you for your reply.  We are trying to initiate a desktop session on this machine so that we can launch a browser session on the machine.

---

### Post by TheFu on 2021-08-01
> **stephenstark said:**
> Thank you for your reply.  We are trying to initiate a desktop session on this machine so that we can launch a browser session on the machine.

You don't need a full desktop to do that. From your workstation, run 
```
ssh -X {remote-user}@{IP}  firefox  &
```
An exact example is:
```
 ssh     -X    thefu@regulus    /usr/bin/firefox  &
```
I exaggerated the spacing. 1 space or 50, doesn't matter. The places without a space cannot have any.

This is 1000x easier than setting up VNC.
Of course, ssh has to be setup on both sides, but ssh is a base tool for all Linux systems anyways.

You could also run the browser locally, but use an ssh tunnel/proxy that ends on the remote system so that all your traffic appears to come from that location. This is handy too. I use both multiple times a week, but mainly the **ssh -X** method is used daily, all day, for almost any program.

---

### Post by ActionParsnip on 2021-08-02
Why launch the browser on the machine? Is it accessing websites which are accessible via [http://localhost](http://localhost) ? If so then just put [http://IP.of.remote.system](http://IP.of.remote.system) and it'll work. Obviously add port numbers and so on. You don't need VNC if you are just accessing a Web page on the remote server side.

---

### Post by TheFu on 2021-08-02
> **ActionParsnip said:**
> Why launch the browser on the machine? Is it accessing websites which are accessible via [http://localhost](http://localhost) ? If so then just put [http://IP.of.remote.system](http://IP.of.remote.system) and it'll work. Obviously add port numbers and so on. You don't need VNC if you are just accessing a Web page on the remote server side.

Or use an ssh SOCKS5 proxy via ssh, if the webapp on the other machine will only bind to localhost.  That's not hard.

```
#!/bin/bash
PORT=64001
SSH_SRV=remote.example.com
   /usr/bin/ssh  -f -C -D $PORT  $SSH_SRV  -NT &

# Star chromium, SOCKS proxy
sleep 3;
echo "Starting chromium proxy "
export http_proxy="socks5://localhost:$PORT "; 
chromium-browser   --proxy-server="socks5://localhost:$PORT " &

```

That is a simplified version of my proxy script to make it easier to understand.  It leaves the ssh connection running. In the real script, I check if there is already an ssh connection on $PORT and reuse it.  Also, I have a ~/.ssh/config file to connect to $SSH_SRV using ssh-keys for authentication. Very convenient. I don't get bogged down in ports, usernames, keys, or other connection details in this script.

---

### Post by ActionParsnip on 2021-08-04
Sounds like I'm really anti VNC if you read other posts but people use VNC when it simply isn't needed. Rather than considering options people seem to just think "I'm accessing a remote system.... Better go find a VNC guide"

---

