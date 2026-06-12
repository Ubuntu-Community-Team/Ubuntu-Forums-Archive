---
title: "Dynamic DNS and SSH"
date: 2011-04-30
forum: Desktop Environments
---

### Post by lucacerone on 2011-04-30
Hi everybody,
I'm trying to configure my desktop
so that I can access it through ssh even when I'm not
at home.
I've created an account on [www.dyndns.com](www.dyndns.com) so that I can (in theory)
access my computer through mycomputer.dyndns.com.
I set up my router and effectively the information about my ip
are updated.
Now it comes the problem (I'm not a big expert of routing and stuffs,
so please don't blame me too much if I write or ask silly questions,
just try to explain it to me :))
I'm not succeeding in making it work and I'd really like to.

As far as I know the things should work like this (tell me if I'm wrong)
when I issue the command
ssh [email]luca@mycomputer.dyndns.com[/email]
a request for ssh connection is issued on the port 22 of my router.
In theory if the router is setup fine the packet is forwarded to the right
pc (I've 3 computers at home but I want to access only one through ssh..
so I forwarded port 22 to the local ip of the computer I want to access).
The computer receives a request on port 22 (the one listening for ssh)
check the password and so on and accepts or refuses the connection.
Is it right?

Now, I have a few question:
first just assume I want only a computer accessible through ssh.
1) What if I don't want to use port 22? but say 55345? 
I guess I have to change something in openssh server configuration file right? (and of course open the port on my router and forward it correctly)
2) is that enough?
3) What if later I want to make the other computers accessible?
Do I have to just install openssh and make them listen on different ports?
4) what about third level domain? can I make so that I access
the different computers by using computer1.myhomecomputer.dyndns.com etc?

Thanks a lot in advance for your help, 
Cheers, -Luca

---

