---
title: "SSH - Cannot connect to server -- always timeouts"
date: 2005-05-20
forum: Desktop Environments
---

### Post by veraction on 2005-05-20
So, I just  installed openssh-server on my one computer. Now I'm trying to connect to it using it's IP, but all I get is timeouts after about 30 seconds. I can successfully connect to other computers, but not mine.

Server is Ubuntu 5.04 with openssh-server
Client is a fresh install (15 min ago) of Ubuntu 5.04

I also tried connecting to it via putty on my windows box, but it timed out too.

Any Ideas?

---

### Post by Sam on 2005-05-20
[QUOTE=veraction]So, I just  installed openssh-server on my one computer. Now I'm trying to connect to it using it's IP, but all I get is timeouts after about 30 seconds. I can successfully connect to other computers, but not mine.

Server is Ubuntu 5.04 with openssh-server
Client is a fresh install (15 min ago) of Ubuntu 5.04

I also tried connecting to it via putty on my windows box, but it timed out too.

Any Ideas?[/QUOTE]
Install nmap package and run
```
$ nmap <ip>
```
to list the available services on the computer. If ssh (port 22) is here, there is probably a configuration error.

If it doesn't appear on the list, ssh is installed wrong or there is a firewall.

---

### Post by veraction on 2005-05-20
OK, I just installed nmap on client and ran the command. It said that the server might be down/not accepting messages. I can ping it fine, but can't do much else I guess.

I'm not sure what firewall software I'd have running if I have default installation, but I'll check it out..

[edit] Maybe it's something my ISP is blocking? It's just a standard Adelphia Cable connection..

---

### Post by Sam on 2005-05-20
[QUOTE=veraction]OK, I just installed nmap on client and ran the command. It said that the server might be down/not accepting messages. I can ping it fine, but can't do much else I guess.

I'm not sure what firewall software I'd have running if I have default installation, but I'll check it out..

[edit] Maybe it's something my ISP is blocking? It's just a standard Adelphia Cable connection..[/QUOTE]
Is your server on your local network ? Is so, your ISP isn't responsible.

---

### Post by veraction on 2005-05-20
well, the two computers are roughly 2 feet away :) however, I don't have a network set up. They both just connect to router for cable internet...

---

### Post by Sam on 2005-05-20
[QUOTE=veraction]well, the two computers are roughly 2 feet away :) however, I don't have a network set up. They both just connect to router for cable internet...[/QUOTE]
If you can ping each other, it should not be any problem to connect them with ssh.... You said you've installed your server with the default installation, but which distro ? Also make sure that there is no firewall.

EDIT: Just read again you first post... Ok you're using Ubuntu as server... Did you use the server installation (typed "server" on install boot) ? I don't know if it installs a firewall.

---

### Post by veraction on 2005-05-21
No, I didn't type 'server' on setup. Both are really just regular desktops, but one has the openssh-server installed on it.

I'll keep trying I suppose.

[edit] Okay, well I think it is a stupid mistake on my part. Just went to [whatismyip.com](http://whatismyip.com) for both computers, and it says they have the same IP. I guess this is logical since its a cable internet connection & I'm just using a router to split the connection.

Still have no idea though. How embarrassing  ](*,)

[edit2] Okay, now I'm able to connect to the server from the other computer using the default router IP thing (192.....) but I'm not sure how i'd connect from some other location through the internet.

---

### Post by cwaldbieser on 2005-05-21
Your two home computers plugged into the router are part of the same local network, right?  If you do an ifconfig for each (assuming they are UNIX based) or an ipconfig (windows based), they both should have IP addresses on the same network (the first 2 or 3 numbers in the quad are the same).

Your router is what is connecting to the Internet, and that is why you see the same IP address from Whatismyip.  Your local PCs are using the router as a gateway.

Is your router set to forward port 22 traffic to your Ubuntu machine?  That is what you need to do if you want to connect to it from some place outside of your local network.  You ssh to the router's IP on the Internet, and it forwards that traffic to a machine on your local network.

Lots of routers are configured differently, but most of the ones I have seen can be accessed by HTTPing to their IP address.

Does that make sense?

---

### Post by veraction on 2005-05-21
Ok, thanks for the info. I just added a custom port forwarding for port 22 on my router and now I can use the actual IP address to SSH into the server, however it seems to lag a lot, like 5-10 seconds delay in displaying what I just typed on the terminal.

But it seems to work ok. Thanks for the help ;)

---

