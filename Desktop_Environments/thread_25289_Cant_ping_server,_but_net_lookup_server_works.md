---
title: "Cant ping server, but net lookup server works"
date: 2005-04-09
forum: Desktop Environments
---

### Post by toggle on 2005-04-09
I have a home network with a server running Clark Connect.

When I boot to windows I have not problem pinging the server using its host name "server".

When I boot ubuntu hoary with samba installed I have an Icon on the desktop that allows me to navigate the directory structure on the server and access files.

I can ping the server using numerical IP address and if I enter: "net lookup server" I am returned the numerical IP address of the server.

However... if I enter "ping server" I get "unknown host server"

What I am really trying to do is move my Thunderbird email onto my server and I need to edit the config file to point to the server i.e. //server/shared... but I can't get there - I could try the numerical ip but that is really not the best thing to do in case I need to reboot the server and it picks up a new IP.

Any suggestions appreciated.

---

### Post by edubarr on 2005-04-09
Just add an entry to /etc/hosts with the ip of the server followed by the alias. Use the other entries there as an example.

This won't help you with dynamic ip issues, though... You could probably assign a static ip to the server.

---

### Post by toggle on 2005-04-09
Thanks... but I believe this is a simple configuration issue (possibly the way I have set up samba) I really want a dynamic dhcp setup and it should be possible.

It makes no sense to me that "net lookup server" results in a resolved IP yet entering "ping server" does not.

[QUOTE=edubarr]Just add an entry to /etc/hosts with the ip of the server followed by the alias. Use the other entries there as an example.

This won't help you with dynamic ip issues, though... You could probably assign a static ip to the server.[/QUOTE]

---

### Post by toggle on 2005-04-10
bump... 

Anybody???

---

