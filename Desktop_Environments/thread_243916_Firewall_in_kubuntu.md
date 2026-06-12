---
title: "Firewall in kubuntu"
date: 2006-08-25
forum: Desktop Environments
---

### Post by marcostt on 2006-08-25
Is there a firewall running by default in kubuntu dapper?

I have problems with amule and the router is well configured, and somenone say to me that probabily there is some firewall stopping the conexions...

---

### Post by Ziox on 2006-08-25
> **marcostt said:**
> Is there a firewall running by default in kubuntu dapper?

I have problems with amule and the router is well configured, and somenone say to me that probabily there is some firewall stopping the conexions...

I believe that Ubuntu and any linux distrobution has a built-in firewall that's in the kernel.  It's called iptables...so I would suggest do a search on iptables and see if you can open the port you wanted.

btw, if i remember correctly, by default, Ubuntu closes all ports except for a few essential ports...

---

### Post by steve.horsley on 2006-08-25
Default Ubuntu installs a firewall (it's built into the kernel, you cannot fail to install it), but does not configure any filtering. I imagine that Kubuntu is the same. 

You can see if there are any filters running with the command
> sudo iptables -L
and an un-filtered PC looks like this:
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


---

### Post by marcostt on 2006-08-26
Thank you, and yes, my Pc is un filtered... then I have no idea about the problem with amule...

---

### Post by hraposo on 2006-08-26
Try to install lokkit
apt-get isnatall lokkit
and execute lokkit as root for disable firewall

---

### Post by steve.horsley on 2006-08-26
Do you have an external router running address translation? If so, you will need to find what port numbers amule uses and arrange for the router to forward incoming connections to your PC. 

You can see that ports Linux is listening on with the command:
> netstat -lnut

---

### Post by marcostt on 2006-08-26
Ok, thanks... I think that could be the problem... I did open the ports in the router interfaz, but maybe some data are wrong... how can I know the "server ip adress" in order to open theses ports?

---

