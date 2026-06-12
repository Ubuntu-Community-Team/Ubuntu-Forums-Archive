---
title: "Probably Network problem. !!"
date: 2009-04-07
forum: General Help
---

### Post by KiwiMate on 2009-04-07
Hi All.

I need your help to solve a problem that I'm having.
Let me explain.

I have a few websites on my own server hosted by and located in the secure datacenter of an ISP.
As the bills are climbing to high ($700.00 each month) I decided to have my own servedr at home on my local network which network has access to the internet through a RTA300 Dynalink ADSL Router.

I gave the new server the internal IP address 192.168.1.200 and on the RTA I created an DMZ pointing towards IP 192.168.1.200

I can access the server from my computer (windows) by typing [http://192.168.1.200](http://192.168.1.200) and everything seems to work fine.

I transferred the first website from my remote server at my ISP to my local server. The domain lookup is updated and the DNS points now to my (RTA300) external IP number. 

Now a strange thing is happening.
Accessing the website from an outside computer works fine.
All the images and links are working and are displayed correctly.

However when I type the URL in on my computer on my local network, I don't see the website but instead I see the internal website of the RTA300 router. 

I tried to change nearly every setting on the router, as I think it is a router issue, but no success at all.

As from the outside, everyting is working fine, it can not be a website issue but it must be a network issue.

Where did I go wrong? Do I have to throw out the RTA and get something else?

Any help in this would be very much appreciated. !!!!

---

### Post by ryanhaigh on 2009-04-07
The router is responding to the request because you are making it from the internal network. If you are making the request from the net the router forwards to the DMZ making it look as though your server is at that IP, in reality it is the router that is at that IP. This forwarding doesn't occur when you are on the internal network, the router recognises the request IP as being its own and responds accordingly.

The only thing you can really do is add an entry to the /etc/hosts for each computer that is on the internal network so that the domain name resolves to an internal ip.

eg. 192.168.1.200    my.server.name


[DISCLAIMER: not an expert]

---

