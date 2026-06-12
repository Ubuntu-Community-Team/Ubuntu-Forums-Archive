---
title: "problems sending files using aMSN and gaim"
date: 2006-09-16
forum: Desktop Environments
---

### Post by gironja on 2006-09-16
Hi!

I know that there's some other posts in this regard, but there I couldn't find any answer for mine.

I will talk as a first person, but the issue is on my gf's Laptop, not on mines. (Yes, I know this forum is for desktop, but laptop's is hardware-related, so I thought that tis might fit in here...)

I'm using a wireless connection trhough an USR5461 router, and I can recieve incomming files throu aMSN and gaim. But when it comes to send files, none of them wanted to do it, telling me that I'm behind a firewall that don't let me send files, or something like that (I can't exactly quote it, since I'm not in the problematic PC right now... sorry...). And the PC is not using any firewall; only the router does.

I solved the gaim issue enabling "Manually specify range of ports to listen on" at Tools->Preferences->Network->Ports. Although it was fixed, I've included here for anyone who might have the same problem... as a psibility for them.

But at aMSN the story is different. It' don't have such an option. I went to it's forum, and I found:

> 
Q: I'm using amsn behind a firewall, or using IP-Masquerade. Sending files
won't work, can I fix it?
A: Maybe the firewall is blocking incoming connections. File transfers work
this way: When you want to send someone a file, you send an invitation with
your IP address and a port number. Then the remote client must connect to
your IP:port to start the transfer.
The used port is usually 6891, 6892 and so on (first transfer is on port 6891,
but if you start a new file transfer while the first one hasn't finished yet,
then it will use 6892, and so on).
So, if using a firewall, you must make sure that it allows incoming
connections to port 6891 (and next ones if you want to be able to make more
than one transfer at the same time).
If you're inside a private network with private addresses, like 192.168.0.x,
then it's more difficult to make file transfers work. You need to send the
real internet address (you can enter it manually or tell amsn to guess it
from a web page), instead of the internal address, and tell the gateway (the
computer with direct connection to the internet) to forward incoming
connections to port 6891 to your computer inside the private network. 


but I can't figure out how can I do that. I think it is an issue in the router itself, so I chek at its webpage, and also wrote an email to their support, but it hasn't been answe yet. 

So I'm here searching for any alternative to my problem, since I know many of you have much more experience that I in Linux OS and its fixing than I have.

Thanks for the help ypu can bring (and sorry for the long post :( )


jNa

---

### Post by seriousstorm85 on 2006-11-22
Ok, in Amsn, open the preference window and go to the connections tab.

See if the transfer port has 6981 and if its ticked.

If so, do u have a firewall on ur Linux OS.

If so add a rule in the incoming services to "Allow" all incoming connections to port 6891.

Restart Amsn and test if a friend can recieve a file u send.

---

### Post by seriousstorm85 on 2006-11-22
An easier option is if u have a firewall, just stop it, launch amsn and see if dat works. If it does, then add da rule when turning ur firewall back on

---

