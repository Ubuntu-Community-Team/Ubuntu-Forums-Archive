---
title: "Internet connectivity Ubuntu 8.04 TLS issues"
date: 2009-05-14
forum: General Help
---

### Post by vasquezj on 2009-05-14
I installed the Ubuntu 8.04 into a Dell Optiplex EX170 and I am not able to connect to the internet. This behaivor is the same regardless of setting the network on remote, dhcp or static. 
 
In each configuration, I am able to ping the internal subnet and internet (i.e. pinging [www.yahoo.com]("http://www.yahoo.com/") and [www.google.com]("http://www.google.com/")). But when I try to get updates for the system, the system is not able to reach the sites. All ubuntu sites are able to be resolved by the DNS and they can be reach by pinging from a terminal. 
 
I have tried all that I can think of but I am still unable to reach the internet through firefox. 
 
I would appreciate any ideas.... 
 
P.S. Firefox is able to open internal sites (intranet).. Also, ethtool and lshw -C network shows that the OS was able to recognized the hardware and applied the respective drivers.
 
Thanks ...
 
Jaime :confused::confused:

---

### Post by petrus4 on 2009-05-14
> **vasquezj said:**
> I installed the Ubuntu 8.04 into a Dell Optiplex EX170 and I am not able to connect to the internet. This behaivor is the same regardless of setting the network on remote, dhcp or static. 
 
In each configuration, I am able to ping the internal subnet and internet (i.e. pinging [www.yahoo.com]("http://www.yahoo.com/") and [www.google.com]("http://www.google.com/")). But when I try to get updates for the system, the system is not able to reach the sites. All ubuntu sites are able to be resolved by the DNS and they can be reach by pinging from a terminal. 
 
I have tried all that I can think of but I am still unable to reach the internet through firefox. 
 
I would appreciate any ideas.... 

Firefox has been screwy with me before; it's been able to connect to sites when tracepath says it shouldn't, altho I might have been getting stuff from an ISP proxy.

If they're reachable by pinging, try tracepath as well.  If that works, you've got problems relating to specific protocols (net applications) or blocked ports.  I have no clue what synaptic runs on.

If you've got access to the net from another machine, or can get it, download [Nmap]("http://nmap.org/download.html"), and use it to check your ports.  80 being closed would affect Firefox.

Check for a running firewall as well; not sure what Ubuntu's is called.  Ufw I think.

---

### Post by vasquezj on 2009-05-14
I checked and I do not have the firewall enabled. Even more frustrating, I just enabled the VNC and I am able to connect to the system remotely but yet I can not browse the internet. I am able to browse internal sites so port 80 is opened.

---

