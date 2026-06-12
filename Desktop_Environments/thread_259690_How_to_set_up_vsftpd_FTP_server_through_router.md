---
title: "How to set up vsftpd FTP server through router"
date: 2006-09-17
forum: Desktop Environments
---

### Post by Sureshot324 on 2006-09-17
I have vsftpd server set up on my ubuntu box and it works fine for my local network.  However, I want to be able to access the FTP server from outside my network.  How do I set this up?

Is it as simple as setting my router to forward port 20 to by Ubuntu box?  If so, will this effect outgoing FTP connections on my Windows box?

---

### Post by Sureshot324 on 2006-09-18
No one knows?  There has to be a way to set up an ftp server behind a router.

---

### Post by RaoulDuke on 2006-09-19
I've been trying to do this in 5.10 as well as in Windows. Still haven't had much luck as of yet. Do let me know if you figure this out, as I will you.

---

### Post by Fibonacci on 2006-09-20
Tried port 21? It works for me on Fedora Core - at least for anonymous FTP.
As for the effect it would have on your Windows box, I don't know, I haven't tried - or, for that matter, ever needed to try.

---

### Post by odinfromvalhalla on 2006-09-20
if the router is running also a ubnuntu (or any linux flavour :P) you can try doing some iptables ;) :

iptables -t nat -A PREROUTING -p tcp -i eth0 -d <router ip goes here> --dport 21 -j DNAT --to <your ip goes here>:21
iptables -A FORWARD -p tcp -d <your ip goes here> --dport 21 -j ACCEPT

---

### Post by Fibonacci on 2006-09-20
And if it doesn't, you can always go [http://www.portforward.com/routers.htm](http://www.portforward.com/routers.htm) and search for your router ;)
But since you have forwarded port 20 to your machine, you've probably already gone through that.

---

### Post by RaoulDuke on 2006-09-20
Well I can't seem to get anything to make a connection. I am trying to have this ANON FTP Server open to the Internet. I think that my ISP may be blocking the FTP ports, How would I go about having vsftpd use a different port? (ex. port: 1984)

---

### Post by Sureshot324 on 2006-09-25
I started forwarding port 21 in addition to port 20 and now it works perfectly.

---

### Post by K.Mandla on 2006-10-01
I've got ports 20 and 21 directed to my server, and I can access it from work and my brother can get to it from across the state. I suppose it will depend on the router, though.

---

