---
title: "Azareus won't download"
date: 2008-02-21
forum: Desktop Environments
---

### Post by eeefresh on 2008-02-21
I am able to open a torrent in Azareus, but after that nothing happens.  No downloading or uploading at all, although it is detecting the numbers of seeds and peers.  

Thinking it might be a firewall setting, I installed Firestarter, but I don't know how to configure it to allow Azareus to work. I also found[ this tutorial]("http://portforward.com/english/routers/port_forwarding/Netgear/WGR614/default.htm") on port forwarding for my specific router, but I am not sure if I need that or not.  Any advice?

---

### Post by eeefresh on 2008-02-21
UPDATE:  I just ran the NAT/Server Port test in Azareus and got this:

Testing port 62022 ... 
NAT Error - Connect attempt to XX.XXX.XXX.XXXXX (your computer) timed out after 20 seconds. This means your port is probably closed.

So how do I open the port?

---

### Post by eeefresh on 2008-02-21
Another addendum:

When I go through the port forwarding walktrhough for my router (linked above), I get stuck on this last part:

If you are forwarding a single port, enter that port number into the Starting Port and the Ending Port boxes. If you are forwarding a range of ports, enter the lowest number of that range into the Starting Port box. Then enter the highest number of that range into the Ending Port box. **Enter the ip address to forward these ports to into the Server IP Address box. If you are forwarding ports so you can run a program on your computer, you should enter your computer's ip address into that box. When you are finished, click the Add button.**

If I am trying to share files with Azareus, what do I put for the servie IP address?  Is this my own address?

---

### Post by imoatama on 2008-02-21
Yes, this is your own address. You will probably also want to set up a static IP in the DHCP table of your router so that the port forwarding consistently goes to your machine.

Btw, this doesn't really belong in the desktop environments forum - it is for things relating to your desktop environment such as gnome, kde etc. Mods feel free to move.

---

### Post by eeefresh on 2008-02-22
My mistake, sorry!

---

### Post by shazzy on 2008-03-15
Yea I had the same problem at first.  I had to go into my router's settings (Linksys) to forward port 29982 (default for Azureus) to my computer's ip address (192.168.1.100).  Now everything's working great!  

P.S. I love Azureus.  It's better than any other torrent program I've seen.  Good interface, a lot of options, but simple.
:)

---

