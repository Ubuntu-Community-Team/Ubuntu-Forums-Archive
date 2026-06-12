---
title: "Remote xwindows without installing xwindows on linux?"
date: 2014-01-27
forum: Desktop Environments
---

### Post by sweddle on 2014-01-27
Hello,

I'm kinda new to Linux and I'm not use I understand they ways I can use remote xwindows..

So my boss wants us to run Linux without any graphical apps on the servers, but I have a need as that it may easy my life a bit. 
- Do I need a xwindows GUI installed on Ubuntu to be able to connect to that server whit something like xming or other RDP app??

Thanks
Shane

---

### Post by TheFu on 2014-01-28
[http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) explains how to run remote applications with X.
If you are on the same LAN, just use X - not RDP.  Xming is for Windows, right? 

The easiest answer is to run X through an ssh tunnel ... 

ssh -X userid@remote-server name-of-program-on-remote-server
Setting up ssh-keys and the ~/.ssh/config file will make your life much easier too.

Use **ssh-keygen** to make the keys on the desktop/laptop you sit at.
Use **ssh-copy-id** to push the public key to the remote-server.
Use **ssh -X** to have all X/Windows traffic transfered through a secure ssh tunnel between the X-server (running on your local PC) and the X-client running on the remote-server.

Clear as mud?  Here's a concrete example:
```
ssh -X thefu@server /usr/bin/xterm -sb &
```
I like xterms over "terminal".  From that xterm, you can launch any GUI program installed on the server to be displayed on the PC you are sitting at.  You can also run the GUI program directly, instead of using the xterm.  A wired network is needed and doing this over the internet is not going to work too well.  For remote GUI programs over the internet, I use NX.   FreeNX is the server and qtnx is the client. But that is a differnt question - completely.

---

