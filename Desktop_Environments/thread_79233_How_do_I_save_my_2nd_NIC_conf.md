---
title: "How do I save my 2nd NIC conf"
date: 2005-10-19
forum: Desktop Environments
---

### Post by billiejoex on 2005-10-19
Hi all. I got two network interfaces: a public and a private one. 
The public interface automatically gain ip and netmask by my ISP. 
The second one needs to be manually configured (ifconfig 10.0.0.1 netmask 255.0.0.1 up). 
Every time I restart my distro this configuration is lost and I need to manually confire my NIC again. 
How can I save that configuration? Wich file do I have to edit? 

Best regards.

---

### Post by chanders on 2005-10-20
I dont have two network cards in my machine but I think you could use the networking tool in Gnome and enter the configurations there. They should be saved when you exit.....

System --> Administration --> Networking

---

### Post by billiejoex on 2005-10-25
I would like to do it by command line, if it is possilbe.

---

### Post by gfarrow on 2005-10-27
Edit the file "/etc/network/interfaces".  This lists all the network interfaces on the system.  List your interface on the "auto" line if you want it brought up automatically by the networking scripts.

Try "man interfaces" for more info.

---

### Post by billiejoex on 2005-10-27
Thank you. It works.

---

