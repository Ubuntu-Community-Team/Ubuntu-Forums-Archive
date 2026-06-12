---
title: "A security thought"
date: 2006-09-03
forum: Desktop Environments
---

### Post by elpuerco on 2006-09-03
I read that I dont need a virus scanner or firewall in Kubuntu?

When in Windows XP at work (on this laptop) I am behind corporate firewall and have SOPHOS anti vurus.

When in Windows XP at home (on this laptop) I am behind corporate firewall when on VPN and have SOPHOS anti vurus and ZoneAlarm Pro.

But when in Kubuntu I have nothing, therefore is it not possible for a hacker to get onto my laptop and access my Windows XP partition when I have it mounted?

Firewalls/virus blocking has never been my strong point!!

---

### Post by Titan_Prometheus on 2006-09-03
You bring up a good point, yes. The reason lies in many aspects. one is that you are not(should not) be running as root, their for even if a virus does get downloaded to your ubuntu partition, it can't execute because it won't have the proper permissions. Another is that about 99% of viruses and malware are for windows, so you can't execute them on linux. It is safe practice though as you said to put a firewall up, even though Linux is one of the most secure OS's out their. 

```
sudo apt-get install firestarter
```

This will download a firewall which you can find in the system tools menu. Also, someone would have to be root in order to mount your windows partition, and the only way they can do that is if you let them. Any other questions?

---

### Post by az on 2006-09-03
> **elpuerco said:**
> I read that I dont need a virus scanner or firewall in Kubuntu?

...

But when in Kubuntu I have nothing, therefore is it not possible for a hacker to get onto my laptop and access my Windows XP partition when I have it mounted?


If you were running windows, you would run a much greater risk of someone actually being able to hack you box in the first place.

In a default ubuntu or Kubuntu install, there is no way for anyone to get into your box.  Nothing listens to the network.  

This is open-source software.  It is pretty unlikely that someone will be able to upload malware into the archive for anyone to install.

So don't worry about your XP partition. 

Just keep up-to-date with software updates.  You do not need a firewall.  You do not need any antivirus.  All that crap is ridiculous.  I don't know how people live with that stuff.

---

### Post by elpuerco on 2006-09-04
OK thanks chaps I shall take this on board. =D>

---

### Post by anaconda on 2006-09-04
Actually ubuntu has "firewall" (called iptables) already installed.. that is one reason why ubuntu is safe..

Firestarter is just a graphical interface for configuring iptables..

---

### Post by az on 2006-09-04
> **anaconda said:**
> Actually ubuntu has "firewall" (called iptables) already installed.. that is one reason why ubuntu is safe..


No, not at all.

The kernel routes packets.  It uses Iptables to tell it where to route them.  By default in Ubuntu, there are no rules set up that are relevant to security.  Again, by default, there is no application that listen to the outside world for connections.

That has nothing to do with iptables.

---

### Post by anaconda on 2006-09-04
Thanks for correcting me..

I will educate myself more about this.

---

### Post by Titan_Prometheus on 2006-09-04
> **azz said:**
> If you were running windows, you would run a much greater risk of someone actually being able to hack you box in the first place.

In a default ubuntu or Kubuntu install, there is no way for anyone to get into your box.  Nothing listens to the network.  

This is open-source software.  It is pretty unlikely that someone will be able to upload malware into the archive for anyone to install.

Just keep up-to-date with software updates.  You do not need a firewall.  You do not need any antivirus.  All that crap is ridiculous.  I don't know how people live with that stuff.

I wouldn't say their is no way for anyone to get into the box. Their are plenty of linux exploits out their, if linux was 100% unhackable then all servers would be run on it. The difference is that linux is build better and safer, not 100%, no box can ever be 100% except the one that is turned off.

---

### Post by skymt on 2006-09-04
A Linux with nothing listening to the network, which is how Ubuntu comes by default, is really, really, 100% unhackable. Unless you count denial-of-service attacks, which can't be defended against.

---

