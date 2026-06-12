---
title: "GDM XDMCP Secure Remote Connections"
date: 2006-07-24
forum: Desktop Environments
---

### Post by awd-s on 2006-07-24
I understand that XDMCP is inherently insecure, but the GDM documentation indicates that if GDM is compiled with the -enable-secureremote flag set TRUE then it will establish Secure Remote Connections via SSH and XDMCP as long as SSH is installed on both the client and the server machines.

Is the Dapper Drake distribution of GDM compiled with the -enable-secureremote switch set TRUE?

Is there a way to prove that this is so on my machine?

Thank you.

---

### Post by MattJ100 on 2006-10-10
Hmm, I have the same question. Is XDMCP secure? If not, in what way?

---

### Post by awd-s on 2006-10-10
Since I posted my query, I think I have an answer. Security of GDM XDMCP depends on the setting of a compile-time flag and the presence of SSH. Since I am unable to determine the true security status of the Ubuntu implementation I decided to assume that XDMCP is insecure and to refrain from using it, which is a pity because it is easy to use. Normally, XDMCP network traffic is broadcast in clear and, therefore, vulnerable to network sniffers.

During my research into this problem, I found that SSH is capable of forwarding X11 traffic across the encrypted channel. I installed OpenSSH on my Ubuntu boxes. Now I can manage my other machines in a secure environment across the network. I do this by opening a terminal window on local machine, then issue the following command:

ssh -X user@network-address

This connects me to the remote machine with X11 forwarding enabled, where user is my user-name and network-address is in numerical form of [www.xxx.yyy.zzz](www.xxx.yyy.zzz).

Once connected, I run commands to invoke the synaptic package manager, for example, thus:

gksu /usr/sbin/synaptic

This command starts synaptic on the remote machine whereupon the windowing traffic is forwarded via encrypted link to my local machine, appearing just as it does were I to run it locally.

Easy way to remember these commands is to drop icons of your frequently used utilities onto your desktop from the drop-down menus, and then right-click on the icon, go to the launcher tab and copy the command to the clipboard and then paste it onto the command line. It sounds more complicated than it is in fact.

It works like a charm and I can rest assured that the network traffic is properly secured by SSH. I am reading the Nutshell book on OpenSSH to find out if there is anything else of which I need to be wary.

Good luck. OpenSSH is the way to go.

---

