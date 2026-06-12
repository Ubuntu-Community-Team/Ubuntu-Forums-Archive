---
title: "ubuntu firewall?"
date: 2006-03-07
forum: Desktop Environments
---

### Post by jinxjinx on 2006-03-07
Does ubuntu have a firewall? 

Im having trouble setting up Azureus. None of my downloads are connecting, and im using the same port number i was using on windows. 

Also, Im behind a school network. Is it possible for the school to block specifc applications from sending data (even if i change my port numbers)?

Thanks guys.

---

### Post by Zoom8112 on 2006-03-08
Hi,

Did you install firestarter?

---

### Post by jinxjinx on 2006-03-08
nope. So your saying that ubuntu has no default firewall that could be preventing udp packets from comming into port 26000?

---

### Post by Perfect Storm on 2006-03-08
Firestarter is a frontend for iptablets which are installed by default. You need to open up for port 6881 as I recall it.

---

### Post by robert_pectol on 2006-03-08
[QUOTE=Artificial Intelligence]Firestarter is a frontend for iptablets which are installed by default. You need to open up for port 6881 as I recall it.[/QUOTE]
Unless he installed one of the available firewall configurators such as Firestarter, he doesn't need to unblock any ports at all.  Nothing should be blocked in the first place.  It's true that the iptables tool is indeed installed by default.  But it does NOT mean that a firewall ruleset has been configured, or that the default policies have been altered from their defaults.  The default policies are set to, "ACCEPT" for all built-in chains.  Basically, unless you (or a script, program, etc.) specifically alter the default policies and/or add new chains and rules by using the iptables tool, then Netfilter (the kernel's packet filter) will not block any network traffic at all.  By default, Ubuntu does not contain any such scripts or programs so there is no firewall defined on a default Ubuntu install (at least as of the Breezy version) even though it does have the tools and capability to configure one, already built in.

To clear up some confusion, iptables is NOT a firewall.  It's simply a command line tool used for the configuration of one.  Hope that helps.

---

### Post by Perfect Storm on 2006-03-08
Thanks for clearing that out.

---

