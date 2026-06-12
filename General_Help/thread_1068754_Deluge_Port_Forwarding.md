---
title: "Deluge Port Forwarding"
date: 2009-02-13
forum: General Help
---

### Post by Schok on 2009-02-13
Deluge 1.1.2
router wrt54g
port 50505-50510 [port forwarded in the router setting]
UPnP and NAT-PMP unchecked, the rest checked and encrypted

in the deluge preferences, when i check the active port the yellow warning triangle thingy still comes out and below deluge there is still "No incoming connection" message. what did i do wrong here? can anyone help? thanks

---

### Post by blazemore on 2009-02-13
Does your system assign the same IP every startup?
For example, if your router is forwarding the port to 192.168.1.103, and your IP is changed to 192.168.1.102 at next boot, it won't work.

Is it actually affecting your torrent speed though?

---

### Post by Schok on 2009-02-13
yes i am using static ip if that's what u mean. I do check the ip every boot just in case. Its not really slow but its not as fast as it was on windows.

---

### Post by Schok on 2009-02-13
bump.

---

### Post by blazemore on 2009-02-15
Do other torrent clients have the same problem?

---

### Post by johnjohn2 on 2009-02-15
What version are you using?

---

### Post by Schok on 2009-02-15
its stated in my 1st post. deluge 1.12

---

### Post by Ryadt on 2009-02-15
Did you open the ports in your firewall?

---

### Post by Schok on 2009-02-15
yes i did. 

on ubuntu u turned off the firewall, but on the router i opened the ports that are needed

---

### Post by thedaylights on 2009-12-21
Question about opening the ports:

> **Schok said:**
> yes i did. 

on ubuntu u turned off the firewall, but on the router i opened the ports that are needed

I have forwarded my ports in my router setup, I have set up a static IP to forward them to. But how do I open my ports in the firewall?

---

### Post by xx58 on 2010-01-03
:rolleyes:Exactly same problems and How and what I did, results still same - nothing changers.

---

### Post by 3rdalbum on 2010-01-03
> **thedaylights said:**
> I have forwarded my ports in my router setup, I have set up a static IP to forward them to. But how do I open my ports in the firewall?

Forwarding the ports is performed by the firewall.

Does it work with UPnP turned on?

Also some routers may need to be turned off and on again before they will apply some settings changes.

---

