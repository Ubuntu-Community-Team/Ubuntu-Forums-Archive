---
title: "SSH to 2 places on the *other* side of a router"
date: 2006-09-20
forum: Desktop Environments
---

### Post by LotsOfPhil on 2006-09-20
I hope my title is mildly informative.

I have 2 Ubuntu boxes hooked up to a router. One is a server and has most ports forwarded to it, including 22 for SSH. What I want to do is forward another port to the other box so I can SSH into it.

So, remotely, I want to type:
ssh address -p 2201

and get to my non-server box.

I can handle the port forwarding, but don't know what to do to the box. Do I edit the /etc/ssh/sshd_config file?

Thanks!

---

### Post by kick6 on 2006-09-20
> **LotsOfPhil said:**
> Do I edit the /etc/ssh/sshd_config file?

Thanks!

Yes!  I don't have that file sitting in front of me, but there's a place/syntax to have the daemon listen on an alternate port.

---

### Post by NetworkGuy on 2006-09-20
Just a suggestion:

SSH to the first PC and then ssh to the second from the first.  You don't adjust any files and you only open one port on your router/firewall rather than two.

---

### Post by LotsOfPhil on 2006-09-20
Thanks to both of you. I will try out both when I get home (PC #2 is off right now) and let you know what happens.

---

### Post by gumbald on 2006-09-20
I vote the second idea, works just as well. Use that method to access my uni department computers behind the server. It provides an extra level of security in 2 passwords and the fewer ports :)

---

### Post by LotsOfPhil on 2006-09-21
For the record, just put
```
Port XXXX
```
in /etc/ssh/sshd_config and then type
```
sudo /etc/init.d/ssh restart
```
to make the ssh listen on another port.

I ended up just making an alias in the /etc/hosts file for the 2nd computer
```
192.168.1.2 optimusprime optimus
```

---

