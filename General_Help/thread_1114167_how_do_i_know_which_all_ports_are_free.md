---
title: "how do i know which all ports are free?"
date: 2009-04-02
forum: General Help
---

### Post by abhilashm86 on 2009-04-02
by which command can i know which of system port is empty, when i use 

abhilash@abhi:~$ sudo ssh 192.168.1.1
ssh: connect to host 192.168.1.1 port 22: Connection refused
so is port 22 busy or what?
how can i check which port is free?

---

### Post by steeleyuk on 2009-04-02
Two reasons I can think of for a connection to be refused. 1) You don't have an SSH server installed on the machine your connecting to or 2) a firewall is blocking the connection.

---

### Post by abhilashm86 on 2009-04-02
> **steeleyuk said:**
> Two reasons I can think of for a connection to be refused. 1) You don't have an SSH server installed on the machine your connecting to or 2) a firewall is blocking the connection.

1) yes i've installed ssh server on my system,

maybe 2 point is true.......

i was just roaming around with some telnet, ip and ping for sometime, a totaly new to these things, so from my knowledge,

we find our ip address from ifconfig command,
then ping our masked ip address to get ip's from our network,

so how to know about free ports of victim machine?

---

### Post by abhilashm86 on 2009-04-02
problem is i don't know about these things, but i'm getting intrested to know how things work and application. So can you tell how ssh works or give me a link, so i can extend my knowledge of topic:)

---

### Post by kanikilu on 2009-04-02
I'm not really sure how to see if ports are "free", but you can see which ports a machine is listening on with nmap. The basic usage is ```
nmap <ip/hostname>
``` I don't think it's installed by default, but it's in the repos.

From the host you are trying to ssh to, you could also do ```
sudo iptables -L
``` to see the firewall rules...

---

