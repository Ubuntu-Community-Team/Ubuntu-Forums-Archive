---
title: "Remote Desktop with Multi Factor Authentication"
date: 2016-07-28
forum: Desktop Environments
---

### Post by mbrozay on 2016-07-28
Hi all,

I run all my servers on AWS EC2 platform. 99% of servers are command line, but I need one server with a GUI that I can remote to using Multi-factor authentication.
I have tried with xcfe and xrdp, gnome and vnc. I see there might be an option with Unity but only it seems only when logging in locally to the server.

VNC gives you an effective local view, but I don't like it as it is too easy to hijack an open session. If I have logged into the server and somebody vnc's to the server then, they are in my session. 

With a Windows server I was able to use a product that modified the login screen to include a one-time-code input box, but I have searched everywhere for linux and doesn't seem to be anything available.

I have secured the server using ssh with multi-factor, requiring a tunnel to access xrdp, but I want to guard against any running remote desktop service being exploited. 

All help appreciated.

---

### Post by Habitual on 2016-07-28
> **mbrozay said:**
> but I want to guard against any running remote desktop service being exploited. 
Close the port to all but yourself in your AWS Dashboard?
AWS Security Groups...

---

### Post by mbrozay on 2016-08-02
I appreciate the reply, but the question wasn't about firewall rules. It can be taken that only ssh is allowed to that server from my IP. The question is about using multi-factor authentication while using a remote desktop protocol to log onto an Ubuntu server.

Thank you.

---

