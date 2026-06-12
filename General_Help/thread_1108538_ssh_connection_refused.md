---
title: "ssh connection refused"
date: 2009-03-27
forum: General Help
---

### Post by skierik on 2009-03-27
Here is my configuration/problem:

I have an Ubuntu server running a static ip with the ssh server installed.  I can log on to this server if I am on the lan.  Once I try to connect from the wan side of my router I get "connection refused".  However, if I setup another ssh server on my xp workstation, I can connect to this fine from the wan side so my port forwarding on the router appears to be working correctly.  I have also made sure I added the wan ip to my host.allow file but this still doesn't connect from outside.  Is the some global security setting for the ubuntu ssh server that I am over looking?

Thanks in advance!

---

### Post by modmadmike on 2009-03-27
search google for you router brand plus the words IP forwarding and set it up to forward port 22
also you need to set it up to forward the port ONLY to the Ubuntu server's IP  because it sounds to me like your forwarding to the XP machine not the Ubuntu machine.

---

### Post by modmadmike on 2009-03-27
also if you are running firestarter or another firewall it will block SSH ;)

---

### Post by skierik on 2009-03-30
I have it forwarded to the correct ip of the ubuntu machine.  I only change it to my xp box when I want to test another server connection.  

Also, I can connect to the ubuntu ssh session when I am on my lan so I'm sure the ssh server is running correctly, just when I try to route to it from the wan that I get the connection refused.  

Are those firewalls you mentioned running on the ubuntu box?  I have shut off my firewall on the router for testing.

---

### Post by Mister.Vash on 2009-03-30
From your wan connection, you could try a verbose ssh connection  so that you can see more information on what is occurring during the connection.

If you normally try something like the following:
ssh [email]user@hostname.com[/email]


Try instead
ssh -vvv [email]user@hosntame.com[/email]

That will output a whole lot of information about the connection, and should at least show if it is making it as far as your server.  If you don't see anything immediately wrong from that output, you could always post it for someone to take a look at.

---

### Post by skierik on 2009-03-30
great idea, will do.

---

