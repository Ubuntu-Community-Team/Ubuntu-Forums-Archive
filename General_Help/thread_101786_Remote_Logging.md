---
title: "Remote Logging"
date: 2005-12-10
forum: General Help
---

### Post by loafofbread34 on 2005-12-10
Hey,
I want to set up a Counter-Strike server on this box I have sitting here at home. I am planning to put Ubuntu 5.10 on it, and load up the server. 

But I want to be able to put new maps on it, change files, restart the server, etc, all remotley. (Using the terminal on my current Ubuntu 5.10 box) 

So, how can I login to my server box remotly through the terminal as if I were sitting right in front of the server box? It is on a LAN with my computer.

Thanks.

---

### Post by schilcha on 2005-12-10
[QUOTE=loafofbread34]
So, how can I login to my server box remotly through the terminal as if I were sitting right in front of the server box? It is on a LAN with my computer.
[/QUOTE]

Just use ssh. It will drop you on a terminal of your server. 

On a terminal type ```
ssh user@your.server
```. Just supply the username for the remote machine and the server's name of ip-address.

Good Luck

---

### Post by taurus on 2005-12-10
You need to install sshd on your server so you can connect it from wherever you want...  And if you want to ftp to it, then you need to have a daemon running on your server as well.  You can pick either vsftpd or proftpd (which are the two most well known ftp servers).

---

