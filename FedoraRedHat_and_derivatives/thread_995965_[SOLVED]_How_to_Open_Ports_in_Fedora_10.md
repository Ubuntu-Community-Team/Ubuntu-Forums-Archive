---
title: "[SOLVED] How to Open Ports in Fedora 10"
date: 2008-11-28
forum: Fedora/RedHat and derivatives
---

### Post by jseiser on 2008-11-28
Ive never had a problem opening ports before, but for the life of me I cant get ports open on fedora.  I want to open a non standard port for ssh and one for bitttorrent.  I have been in the GUI for their firewall, opened port 9140 tcp and udp, and the port is already open on the router.  Yet, the port is still reported as closed.  Is their an easier way?  I have been unable to find a guide on this.  Thanks.

---

### Post by kabloink on 2008-11-28
The only thing you should have to do in Fedora is add the port in the "other ports" section in the firewall gui and apply the changes.

Did you set up the port forwarding in your router for port 9140?

---

### Post by jseiser on 2008-11-28
Yes both ports on my router forward to 192.168.1.121 which is my static, and when i was on arch that config allowed me ssh to my box.  So I think the router set up is fine.  I must have did something wrong, I will look again when I get off.  does ssh need both tcp and udp?

---

