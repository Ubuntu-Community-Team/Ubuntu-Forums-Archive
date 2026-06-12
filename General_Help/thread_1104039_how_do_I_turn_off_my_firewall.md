---
title: "how do I turn off my firewall?"
date: 2009-03-23
forum: General Help
---

### Post by jitup on 2009-03-23
how do I turn off a TCP-wise and UDP-wise firewall? I am running ubuntu 8.10
thank you

---

### Post by hyper_ch on 2009-03-23
why turn it off? by default it has no rules and hence nothing gets filtered out.

---

### Post by aikiwolfie on 2009-03-23
Actually stuff does get filtered out. Linux has iptable rules built right into the kernel and with the firewall enabled things like SAMBA don't work.

This should help with what you're looking for.

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html")

---

### Post by hyper_ch on 2009-03-23
aiki: by default iptables has no rules setup hence nothing gets filtered...

---

### Post by aikiwolfie on 2009-03-23
The firewall also locks down certain ports required by things like Samba. By default these ports are closed in Linux. Without a firewall present Samba can simply open whatever it needs. When the firewall is running, it needs to be told Samba is allowed to open the ports it needs otherwise Samba can't open the ports it needs and can't find the network. I've tried it.

---

### Post by hyper_ch on 2009-03-23
aiki: the firewall is iptables and as stated before, by default (on ubuntu) it has no rules. When iptables has no rules it means, that nothing is being filtered... if you install then a daemon it will be accessible.

---

### Post by aikiwolfie on 2009-03-23
Dude I've already stated what happened when I tried my self. So whatever. I've already answered the OPs question. You're just trolling.

---

### Post by hyper_ch on 2009-03-23
> **aikiwolfie said:**
> Dude I've already stated what happened when I tried my self.
On a vanilla system? I don't think so... hence your results are not correct.

> **aikiwolfie said:**
> So whatever. I've already answered the OPs question.
Actually, you didn't.

> **aikiwolfie said:**
> You're just trolling.
I tend to think it's the opposite...

Btw, that's what iptables configuration looks on a vanilla ubuntu system like:

> 
hyper@xubi:~$ sudo iptables -L
[sudo] password for hyper:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
hyper@xubi:~$

Now please tell me where anything is being blocked here? I fail to see that...

---

### Post by Nano_ext3 on 2009-03-23
The best thing you can do is mess with

[*iptables]("http://bodhizazen.net/Tutorials/iptables/")
*OR
[AppArmor]("http://ubuntuforums.org/showthread.php?t=1008906")

---

### Post by bodhi.zazen on 2009-03-23
> **jitup said:**
> how do I turn off a TCP-wise and UDP-wise firewall? I am running ubuntu 8.10
thank you

  What are you trying to do exactly ?

As has been stated already, bu default the firewall (iptables) is permissive.

Did you configure it ? if so, how?

What is the output of :

```
sudo iptables -L -v
```

---

### Post by albinootje on 2009-03-23
> **aikiwolfie said:**
> Actually stuff does get filtered out. Linux has iptable rules built right into the kernel and with the firewall enabled things like SAMBA don't work.


This is not correct.
Where is your information based on exactly ?
By default a plain Ubuntu desktop or server installation is *not* firewalling any ports!

---

