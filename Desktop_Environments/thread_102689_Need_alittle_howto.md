---
title: "Need alittle howto"
date: 2005-12-12
forum: Desktop Environments
---

### Post by tellnes on 2005-12-12
Ok, a challenge for the linux gurus out there.

I have at home a ubuntu box, this is located behind a firewall, running on a 192.168.1.x address. Global address is static. I have natted a few ports trough the firewall to my ubuntu box and can nat more.

Now, at work im on a windows Xp mashine, admin rights, on the 10.x.x.x range behind a firewall, with no possibility to nat.

In my previous job, i had a linux guy who helped me get a remote desktop from work to my pc at home using some sort of key,ssh,putty and vnc. This worked great, but i dont remener how to.

Coud anyone who has the knowlede lead me to set up a remote desktop from work to my box at home, using putty, vnc, ssh? Like a walktrough! and i will send the person virtual huggs:) :)

---

### Post by Sjun on 2005-12-22
I am not much of a linux guru, but still will give it a try:

First: make sure you forward the right ports to your ubuntu machine in your router. I forward incoming port 443(usually SSL) to 22(i think, i believe this is  the usual ssh port)
Why 443? because our proxy at work won't block this. it's used for https aswell ;)
then, in putty, Connection, proxy: make sure you have the correct proxy settings to get through.
(mostly HTTP, and the name of the proxy with the port, you should be able to check for these settings in your browser if you're not sure what they are)
And provide your domain\username and password.
In Putty, Connection, SSH, Tunnels: add as source port: 1, Destination: 192.168.1.x:5900, and make sure you hit "add".
Finally, in Putty, Session: Hostname: your home IP-address, port 443 (or whichever you choose), SSH, gave it somekind of name to save, and hit save so you don't have to re-enter everything again, and hit login.
Accept the certificate, provide username/password and fire-up vncviewer.
in vncviewer, connect to 127.0.0.1:1 and login to your machine.

I hope i got everything right, or at least gave you enough pointers to get this done :KS


(First post here) :D

---

