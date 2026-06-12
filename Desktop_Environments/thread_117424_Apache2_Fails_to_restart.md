---
title: "Apache2 Fails to restart"
date: 2006-01-14
forum: Desktop Environments
---

### Post by AusIV4 on 2006-01-14
Hi, I've got a problem.

I'm running an apache2 server on my Ubuntu machine. It works pretty well, except when I find a reason to edit the config files. When I run the command

sudo /etc/init.d/apache2 restart

I get the following error:
```

* Starting web server (Apache2)...                                             
(98)Address already in use: make_sock: could not bind to address [::]:85
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]

```
I run the server on port 85 because my school blocks port 80. Also, I've only noticed this since I started using the Firestarter firewall. I've tried disabling the firewall and restarting apache, but that doesn't seem to solve the problem. When I reboot the computer, everything loads fine.

Any thoughts?

---

### Post by vruum on 2006-01-14
how do you disable the firewall? firestarter is just an iptaples front end, it stays active even after closing down the program

---

### Post by AusIV4 on 2006-01-14
I disable the firewall by hitting the "Stop Firewall" button on the firestarter interface.

---

### Post by AusIV4 on 2006-01-15
Can anyone at least tell me a way to see what ports are listening? That might give me more resources to resolve the problem myself.

---

### Post by cutOff on 2006-01-15
To see what ports are listening

```
lsof -i
```

To change default port for Apache

/etc/apache2/ports.conf

---

