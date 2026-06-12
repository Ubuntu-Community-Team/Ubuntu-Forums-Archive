---
title: "SSH connection not working"
date: 2006-09-13
forum: Desktop Environments
---

### Post by Copps on 2006-09-13
I have installed the SSH server via apt-get.

I can connect to my Ubuntu machine locally in Terminal via

```
ssh -p557 localhost
```

I can connect to my Ubuntu machine from a Windows machine on the same network with Putty by connecting to Ubuntu's local IP address (192.168.x.x) and the port number 557 (I changed this in sshd_config for security purposes).

What I cannot seem to do is connect to my Ubuntu machine from a remote PC, via the internet facing IP address of my home network (I have set up port forwarding on my router to forward connections on port 557 to Ubuntu's internal IP inside my network).

Anyone got an idea on how I can troubleshoot that please?

---

### Post by Jussi Kukkonen on 2006-09-13
From your troubleshooting it looks obvious that the problem is 'before'  your server -- the router or your ISP...

Some things to check:
* Are you sure the external IP you are using is correct?
* try forwarding on another port, you ISP might be blocking ports (try 80 temporarily, that should work...)

---

### Post by wieman01 on 2006-09-13
Since port forwarding is not an issue, I would suggest 2 things:

1. Your Internet servider provider does not allow port 557.
2. You are trying to connect to your own network from your home network, thus the connection going in a loop, correct? 

If 2. is the case, then have somebody else try to connect to your server. I have the same problem... Other people can connect to my FTP server from outside, but when I tried to do the same from within my network specifying my public IP address, I get a timeout.

---

### Post by Copps on 2006-09-13
I'm almost embarrased to reply, but the port I'd specified in ssh_d config (577) was different to the one I was specifying in my remote SSH connection (557). Everything is now running fine, thanks Jussi, for making me realise that double-checking the most obvious of issues is always the best way to go!

---

### Post by wieman01 on 2006-09-13
> **Copps said:**
> I'm almost embarrased to reply, but the port I'd specified in ssh_d config (577) was different to the one I was specifying in my remote SSH connection (557). Everything is now running fine, thanks Jussi, for making me realise that double-checking the most obvious of issues is always the best way to go!
Hahaha... Yes, I'd be embarrassed as well but this kind of thing happens to me all the time. My mom used to say:"Think first, then talk." ;-)

---

### Post by Copps on 2006-09-13
wieman, the lesson has been most definitely learned! ](*,)

---

### Post by wieman01 on 2006-09-13
> **Copps said:**
> wieman, the lesson has been most definitely learned! ](*,)
Happy to hear you are waaay smarter than I am. :-)

---

