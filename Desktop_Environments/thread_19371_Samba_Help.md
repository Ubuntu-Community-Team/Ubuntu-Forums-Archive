---
title: "Samba Help"
date: 2005-03-11
forum: Desktop Environments
---

### Post by maverickapollo on 2005-03-11
I need help on integrating Ubunto with my MS Windows network. (Very mixed!)

Ok, I have a samba server running on the main server, who is a server for the BETEL workgroup.

In Ubunto I can Applications --> run "smb://192.168.1.1/mike" and connect to the share. It however all comes up as read only.

If I go into the Computer --> Network --> Windows Network there is nothing listed at all.

If I install Samba and enable windows networking in Computer --> System Config --> Networking I still can not get to the server share. It does however list this PC as a resource. 

Any one offer any help?

---

### Post by dermotti on 2005-03-11
I had a heck of a time getting my samba working under gnome and when i did ti was very slow. Best luck i had was using smb4k

---

### Post by byourg on 2005-03-11
If you are running a firewall you have to enable the SMB ports, then you will see the window$ network in computer > network.

---

### Post by maverickapollo on 2005-03-12
I realise that, all the ports are open. I am not running a firewall on the desktop machine, the server however is. It has all NetBIOS and associated ports open to lan clients.

---

### Post by Ozitraveller on 2005-03-13
I'm running Firestarter, which ports do I have to enable? I have a Win Xp network and they have firewalls.

---

### Post by byourg on 2005-03-13
[QUOTE=Ozitraveller]I'm running Firestarter, which ports do I have to enable? I have a Win Xp network and they have firewalls.[/QUOTE]

The ports are 137-139. Go to the policy tab and right click the 'Allow Service' box. Click the +Add Rule and the name drop down box, select SMB. 

You need to do this for the inbound and outbound policies.

---

