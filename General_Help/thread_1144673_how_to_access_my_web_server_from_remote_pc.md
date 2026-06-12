---
title: "how to access my web server from remote pc"
date: 2009-04-30
forum: General Help
---

### Post by gfunkera on 2009-04-30
hi guys.. i managed to get my apache2 web server working and i can connect to localhost through firefox.. i designed a simple webpage at localhost and now i wanna access it (on my computer) from my friends house across town.. 

anyone know what i can do? do i just connect to my IP address through his web browser??

---

### Post by trwww on 2009-04-30
> **gfunkera said:**
> do i just connect to my IP address through his web browser??

In general yes... but there are often firewalls in between the two connections.

I'm assuming you have the standard high speed internet -> modem -> router -> computer connection.

First, the IP address you would use is the IP address provided by your ISP, and not any local IP addresses that computers on your LAN may be using.

Next, if your computer is connected directly to your modem, you may need to get a router. It is possible that your modem will do port forwarding for you, but usually they don't.

Now, configure your router to either put the server in to a DMZ environment, or forward port 80 to the server. If you use DMZ, you really should make sure the software firewall in your server is set up and working like you want it to.

Then you should be all set.

---

### Post by gfunkera on 2009-05-01
okay so i have my computer currently wirelessly connected to my router .. and yes i have the standard high speed connection through the router... so luckily for the process of getting this question answered (and luckily for you) i know what you mean when you say DMZ on the router.. the part im getting confused about is how to go about configuring the routers DMZ to work the way you are talking about...

so basically i need a little walk through so that when i am done setting up the DMZ ill have a checklist of what needed to be changed/checked/set ... does that make sense? if not ill clarify... thanks for your time btw... looking forward to your reply...

---

### Post by trwww on 2009-05-01
> **gfunkera said:**
> so basically i need a little walk through so that when i am done setting up the DMZ ill have a checklist of what needed to be changed/checked/set ... does that make sense? if not ill clarify... thanks for your time btw... looking forward to your reply...

Configuring a DMZ in a residential router is really straight forward... you put the IP of the machine that you want to be in the DMZ in the router config. Its not really something that lends itself to me walking you through here. There are plenty of examples on google.

Perhaps if you could go ahead and start trying to do it and then if you get hung up on a later step, come back and describe that specific problem.

Regards,

---

### Post by LiQuidAiR on 2009-05-02
I would recommend setup up port forwarding.  This tends to be more secure than setting up a DMZ.  With port forwarding you have to know what sockets are listening on your Apache 2 server.  In most cases, port 80 (standard HTTP port) and than perhaps port 22 for SSH. SSH is used to give encrypted access to the remote server/workstation thru the command line interface.  It can be used for other services also, but this is what I used it for. 

The main reason I choose SSH over port 22 is because I installed the server edition of Ubuntu.  The server edition does not include a GUI or graphical user interface.  Everything is done thru command line.  Talk about tedious. But, you can really learn alot.

The same principal would apply to forward perhaps remote desktop ports.  This is where you could control an entire machine using a GUI rather than command line.  I don't have the details on this method, though. 

What are you mainly interested in?

---

