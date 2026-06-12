---
title: "SSH Forwarding/Tunneling"
date: 2008-02-11
forum: Desktop Environments
---

### Post by Maconvert on 2008-02-11
Hello,

Linux newbie here. 

I’m wondering if someone could explain how to accomplish SSH forwarding (or is it tunneling?) through an “always on” PC running Ubuntu 7.10.

This is my situation…

I want to SSH into my school computer on port 22 from my work PC (Windoze XP) using “Putty.exe”.
The problem is that my work network blocks all ports except 20 and 80.
Now, at home I have a PC running Ubuntu 7.10 and it is connected to a router that I can configure for port forwarding on any port I want.

So, is it possible to set everything up so that I can SSH through my home Linux PC on port 20 or 80 through to my school PC on port 22?

Please let me know.

Regards.

---

### Post by djgrandmarquis on 2008-02-11
Yes, this should work. And I believe you can accomplish this using the default ssh settings in Ubuntu. In your router, set up a virtual server to forward incoming traffic on port 20 to port 22 on your Linux machine. 

You should be able to set this up by installing the "ssh" package and configuring your router. All the routers I have worked with support this functionality.

---

### Post by Maconvert on 2008-04-11
How do I set up the SSH package?

---

### Post by djgrandmarquis on 2008-04-11
Go to your package manager and install "openssh-server" (and "openssh-client" if not already installed). The "ssh" package may be deprecated in new Ubuntu releases, I'm not sure.

I actually prefer the command line:
```
sudo apt-get install openssh-server
```

---

