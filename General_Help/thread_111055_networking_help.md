---
title: "networking help"
date: 2006-01-01
forum: General Help
---

### Post by sca344 on 2006-01-01
I have a wireless router that I have upstairs and my windows laptop receives that signal. My desktop comp is downstairs. I need to be able to plug my laptop into my desktop with an ethernet cable and have my desktop online. my desktop has kubuntu and its not detecting any networks when connected. I have tried getting admin controls by typing sudo passwd root  and sudo -s _H but that is only giving me admin controls in the konsole. Which i am a newb and do not know how to change settings in that yet. Any help would be appreciated.

---

### Post by Vetto on 2006-01-01
How many network cards are in your laptop? and what type are they (wireless, ethernet, etc)
Are you familiar with what needs to be done and are just unclear how to do it in linux?

---

### Post by emperor on 2006-01-01
[quote=sca344]I have a wireless router that I have upstairs and my windows laptop receives that signal. My desktop comp is downstairs. I need to be able to plug my laptop into my desktop with an ethernet cable and have my desktop online. my desktop has kubuntu and its not detecting any networks when connected.[/quote] 
You will need to connect an ethernet cross-connect cable (not a patch cable) between the desktop's ethernet adapter and your laptops wired ethernet port. Then your laptop will then need to be configured to route the network traffic to the wireless adapter. So essential your laptop will need to be a router. On linux, the routing can be setup using iptables directly or via a software firewall like firestarter.

I would suggest that you install a wireless ethernet card in the desktop; put it directly on the internet via the upstairs wireless router?

If your desktop already has a wireless card and does not work due to a weak signal, then you could install a wireless repeater downstairs to boost the signal. If the wireless router has a removable antenna, then an >db antenna may do the trick.

---

### Post by M4VE on 2006-01-01
sounds like he has his router upstairs, and wants to use his laptop to deliver the network connectivity to his desktop, if I'm reading it right.  Sounds like an awful lot of trouble, even using a crossover cat 5.  I'm not even going to touch that part of the question, but as far as getting admin privelages to do what you want, you could just use sudo to execute the graphical commands you're trying to use, that'll automatically give you admin privs.

---

### Post by Vetto on 2006-01-02
I agree this is going to be a mess...my reccomendation is buy a wireless card for the desktop, or cable it to a port in the router upstairs with cat6.

sca344?  what do you want to do?

---

### Post by sca344 on 2006-01-03
i used a cross over cable and set the laptop up as a server. basically all i needed was the admin controls.. then sudo commands was not working so i fixed that by  reinstalling

---

