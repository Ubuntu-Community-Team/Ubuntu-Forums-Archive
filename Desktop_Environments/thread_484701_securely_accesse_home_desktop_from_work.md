---
title: "securely accesse home desktop from work"
date: 2007-06-26
forum: Desktop Environments
---

### Post by nami on 2007-06-26
Hi

I have ubuntu 7.04 at home and I was wondering if it is possible to access my home desktop from work.  At work I am using windows xp.

Is it possible to somehow access the home desktop securely from work?

Any help will be appreciated

Thanks

nami

---

### Post by dfreer on 2007-06-26
Although this might be a bit more work, you could try this method:
[http://ubuntuforums.org/showpost.php?p=2912038&postcount=7](http://ubuntuforums.org/showpost.php?p=2912038&postcount=7)

EDIT:
Since you are using an XP as the client, you have to spice it up a bit differently. Follow the above guide to set up the server. Then, set up xming so that you can use putty and SSH to secure the connection to your ubuntu desktop.
[http://solaris.reys.net/english/2006/04/x11_forwarding](http://solaris.reys.net/english/2006/04/x11_forwarding)
This should help you with the client side of things, don't worry about enabling X11 forwarding on the SSH server (it is already enabled by default). The only thing that might make a difference is the following line:
```
X11UseLocalhost yes
```
It isn't anywhere in /etc/ssh/sshd_config by default, and with ubuntu to ubuntu remote desktop it is not needed. It might be needed for XP to ubuntu however.

---

### Post by nami on 2007-06-26
thanks for the links.

i am at work at the moment, and was just doing a little background research on my breaktime (i know i'm sad)...

i have a question or 2 about this which are bothering me.

1. at work all our ports are blocked except the http port via some external firewall management company.  will i still be able to remote desktop to my home desktop?

2. if i do this, will the IT Department be able to record what I am doing and login to my desktop without me knowing?

---

### Post by dfreer on 2007-06-26
(1) In general, you should be able to. As long as they are not using a proxy filter that makes all of the web requests for the company, it should work fine. Best way to find out is to try it.
(2) They only thing they should be able to record would be an outgoing communication from your work desktop on port XXXXX (random), with the packet being set to yyy.yyy.yyy.yyy:22 (your desktop machine). They will not be able to login to your desktop without hacking your SSH server, which would be illegal for them to do (it may be illegal for you to contact your home machine from work, and can get you fired from your job).
If you are really paranoid, you could hop your traffic across proxy servers around the world, can't think of the program name right now but from what I remember it had approx. 30 servers to bounce your signal around. This would eliminate their knowledge that you are logging into YOUR desktop, the chances that they feel it is worth the time and cost to trace where the packet went are very slim. Of course, it would probably be nearly impossible for you to use remote desktop at this point.

---

