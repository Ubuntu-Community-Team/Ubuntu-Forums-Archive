---
title: "Firestarter Wizard Questions"
date: 2008-12-21
forum: General Help
---

### Post by kkruecke on 2008-12-21
I have installed Ubuntu on my home pc. My pc is cabled to a linksys router (which is cabled to Verizon Fios). 

Do I need a firewall? 
I installed the Firestart GUI. The Firestarter Wizard asked if I wanted DHCP and Internet Sharing. I did not check either. Should I have?

---

### Post by Shazaam on 2008-12-21
Iptables/ufw is your "firewall". Firestarter is a gui frontend for iptables and it is used for simple iptables rule configuration. DHCP is fine. Leave internet sharing disabled unless you have other pc's accessing the internet from your Ubuntu box (not the Linksys).

---

### Post by lovinglinux on 2008-12-21
You already have a firewall (open by default), which is called "iptables". Firestarter is a firewall manager, which basically means it provides an easy way to create firewall rules for your iptables through a graphical interface. It also provides additional features like real-time connection monitoring and logs.

Once you create the rules in the Firestarter interface you can close it, because the real firewall works in the background. It is actually advised to do so, because the Firestarter GUI runs as root and it has some bugs that could let someone take control of your machine. This is basically why some people do not recommend Firestarter. But if you do not run the GUI all the time you should be fine and Firestarter is great for creating iptables rules without knowing the commands.

You don't need to enable the firewall if you don't open ports in the router and if you don't have services listening to ports, which is the default in a Ubuntu fresh install. Nevertheless, it won't hurt to have the firewall running (if properly configured) and, in my opinion, security is never too much. After all, soon or later you probably will install applications that listen to ports or even open ports in the router like UPnP torrent clients (if you enable UPnP in the router obviously).

Soon or later this thread will be flooded with people recommending Gufw instead of Firestarter because it's new and Firestarter "is not" supported anymore and blah blah blah...If you don't run the Firestarter GUI all the time, for monitoring connections for example, there is no need to use other firewall manager and it will be as safe as any other application, because it's iptables that do the job for all of them.

Nevertheless, I recommend learning how iptables works and how to create your own rules with command-line. This knowledge will give you full control over your firewall and will allow you to decide what kind of traffic to block or allow in any situation, not only those determined by the the firewall managers. For example, Gufw does not allow to block outgoing traffic.

[[COLOR="Red"]**This is**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=159661") a good place to start if you would like to learn about iptables.

---

### Post by kkruecke on 2008-12-22
Thanks for the replies.

---

