---
title: "How to log into x remotely"
date: 2008-08-15
forum: Desktop Environments
---

### Post by lsutiger on 2008-08-15
I was reading [this post]("http://ajopaul.wordpress.com/2007/11/23/remote-login-to-linux-from-windows-non-vnc/") in order to log into a linux box from windows with X.

The only problem is that it does not explain which port X listens to. The computer I will try to log into is behind a firewall.

So...the question is, which port do I open and direct to accomplish this?

---

### Post by bingoUV on 2008-08-15
> **lsutiger said:**
> I was reading [this post]("http://ajopaul.wordpress.com/2007/11/23/remote-login-to-linux-from-windows-non-vnc/") in order to log into a linux box from windows with X.

The only problem is that it does not explain which port X listens to. The computer I will try to log into is behind a firewall.

So...the question is, which port do I open and direct to accomplish this?

Do you seriously have a requirement of non-vnc access? I believe vnc works great, and the argument given here that "unlike VNC where actually you are viewing a already running X session." is totally false. 

Vnc client is freely available for windows and you do not need to open any port in the firewall in the windows machine. You need to open port 5900 (can be changed) for the linux machine on which you run the vnc server.

---

### Post by lsutiger on 2008-08-15
Yes, to have remote users login with their own session.

The question at hand was which port do I open and direct to accomplish this.

---

### Post by wd5gnr on 2008-08-15
Usually port 6000 + screen #. I've done this before, although not lately.

What I usually do not (just added this) is:

ssh -l user -X hostname

Now you have an X session over ssh which is secure and easy to tunnel.

---

### Post by lsutiger on 2008-08-15
Thank you, I will look into it more

---

