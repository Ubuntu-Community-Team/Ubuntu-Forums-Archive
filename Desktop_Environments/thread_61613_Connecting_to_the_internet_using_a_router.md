---
title: "Connecting to the internet using a router"
date: 2005-09-01
forum: Desktop Environments
---

### Post by NoHope on 2005-09-01
Hello all!

I have a DSL-500G modem, which I transformed to a router.

I just can't connect to my internet using this, I don't know how to make it under Linux. Under Windows, I just go to TCP/IP properties and "tell" it to take the IP Adress automaticly... how can I make the same thing in Linux?

Thank you very much. Bye!

---

### Post by built_with_love on 2005-09-01
As long as I know, you're gonna have to tell Linux (please forgive me if I'm wrong) that the IP address of your modem must act as the gateway address. By the way: is the router connected to a hub or is it connected direclty to you NIC?

Cheerz.

---

### Post by NoHope on 2005-09-01
Yes, it's connected to a hub (Actually, a switch).

---

### Post by professor_chaos on 2005-09-01
If your router is configured to DHCP, just set up your network card to the same in System->Administation->Networking

---

### Post by NoHope on 2005-09-01
[QUOTE=professor_chaos]If your router is configured to DHCP, just set up your network card to the same in System->Administation->Networking[/QUOTE]
 Strange... it just doesn't work... and I don't know if my modem is configured to DHCP... is it possible to know?

Thank you! Bye!

---

