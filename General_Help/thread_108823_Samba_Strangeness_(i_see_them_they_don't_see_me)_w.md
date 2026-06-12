---
title: "Samba Strangeness (i see them they don't see me) windows network"
date: 2005-12-27
forum: General Help
---

### Post by mfarquhar on 2005-12-27
i hav an exising lan between three windows ME machines, one daul-boots Ubuntu/Kubuntu and i fought with samba for hours and got some of it working

my machine can see the other computers but they can't see me?
anyone else have this problem

(note: am networking newb, only LAN'ed windows before)8-[ 

any help would be apreciated

---

### Post by Koybe on 2005-12-27
Do you have some share on your samba installation? Did you create a samba user matching one of your ubuntu's user?

And finally... don't use windows network browsing, it's working when it wants ;)

---

### Post by MartinG on 2005-12-27
[QUOTE=mfarquhar]i hav an exising lan between three windows ME machines, one daul-boots Ubuntu/Kubuntu and i fought with samba for hours and got some of it working

my machine can see the other computers but they can't see me?
anyone else have this problem

(note: am networking newb, only LAN'ed windows before)8-[ 

any help would be apreciated[/QUOTE]Have you got the server part of samba installed (samba) or only the client (smbclient)? Only the client is installed by default, which would give the result you describe.

What firewalls have you got running? It's a good idea to disable all firewalls while troubleshooting if it's only a LAN, as this sort of thing is often to do with blocked ports.

---

### Post by mfarquhar on 2005-12-27
i installed whatever samba packages came with the install cd

i don't think i have any firewalls running (have never used any before)

and i'm trying to run Peer-to-peer (no server)

?????

---

### Post by MartinG on 2005-12-28
[QUOTE=mfarquhar]i installed whatever samba packages came with the install cd

i don't think i have any firewalls running (have never used any before)

and i'm trying to run Peer-to-peer (no server)

?????[/QUOTE]The way samba works, though, is on a server-client model (This is is in fact the way almost everything works on linux; for example, even on a stand-alone machine you might have a mail server and a client, to handle messages to you from the system).  

However, don't get the idea that this means one machine acts as a server and all the others are clients; the network is, in effect, peer-to-peer. Thus, on my network of two Linux and one Windows machine, I use samba, and this involves having the samba server package installed on each of the linux machines as well as the smbclient package. If I only had the smbclient installed, my linux machines would each see the windows machine, but they wouldn't see each other (on samba) and the windows machine wouldn't see them.

I think, therefore, you need to enable extra repositories and install the server components of samba, viz:```
sudo apt-get install samba
sudo apt-get install smbfs
```See also
[http://makuchaku.info/amnesty/#sambaserver](http://makuchaku.info/amnesty/#sambaserver)

---

