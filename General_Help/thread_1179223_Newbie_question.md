---
title: "Newbie question"
date: 2009-06-05
forum: General Help
---

### Post by LucaGiudice on 2009-06-05
I have a question: I can't find anywhere what are the meaning and purpose of the "dns-search" command I find in my firewall's \etc\network\interfaces configuration file.

I'm asking because I'm re-setting it up and I'm having some problems in DNS resolution.
dns-nameserver seems to be setted correctly so I'm wondering if dns-search is the cause of my problem.

Thank you in advance for your time.

---

### Post by ARhere on 2009-06-05
Can you be more specific?  When you say, "your firewall's" did you mean your Ubuntu machine or a Linux powered router?

For my Ubuntu machine...
```
$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

```

Of course I am not using a static IP and when I do set a static IP I use the GUI network tool and have never bothered to look at the "interfaces" file.

I know this probably does not help but try using the GUI tools to set a static IP, enter in your DNS servers, and then check the "interfaces" file to learn what is needed.  In 9.04, then System->Preferences->Network Connections.

I am assuming you know your ISP's DNS server IP's.

-AR

---

### Post by LucaGiudice on 2009-06-05
It is an Ubuntu powered PC that acts as a firewall inside my office's network.

It's main purpose is to redirect (prerouting and postrouting) ports from-to our public static IP address. And this is working. 

The thing is not working is pinging named computers (EG: our server has an internal IP address that is 196.100.0.17  if I ping that address from the firewall I get an answer, but if I ping the server by typing "ping servername" i get no answer at all).

So I documented a bit myself (the firewall has been installed by another person that is no more working with me) and went to edit \etc\network\interfaces  discovering that dns-nameservers is correctly configured and there is that dns-search command whose I do not know anything about. I'm just wishing to learn it's purpose and meaning in order to understand if it is the source of my firewall's internal DNS name resolution problems.

---

