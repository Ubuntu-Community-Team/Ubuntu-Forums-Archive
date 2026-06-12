---
title: "ClamAV terminal command, question"
date: 2009-09-22
forum: Desktop Environments
---

### Post by squirtmph on 2009-09-22
I have fiend browsing the internet how to install ClamAV with I have done it using: 
Synaptic Package Manager 
I have installed ->clamav -->clamav-daemon, clamav-freshclam 
and i did this command:
> oem@freekbox:~$ sudo freshclam 
[sudo] password for oem:  
ClamAV update process started at Mon Sep 21 18:16:53 2009 
WARNING: Your ClamAV installation is OUTDATED! 
WARNING: Local version: 0.94.2 Recommended version: 0.95.2 
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq) 
main.cld is up to date (version: 51, sigs: 545035, f-level: 42, builder: sven) 
daily.cvd is up to date (version: 9821, sigs: 79151, f-level: 43, builder: guitar) 
My next step asking me: 
HTTPProxyServer ----> my number 
HTTPProxyPort     ----> My Number 
I did some research how to find my proxy IP Address 
> oem@freekbox:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:11:0a:a4:1e:22   
          inet addr:[COLOR=red]192.168.1.102[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::211:aff:fea4:1e22/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:28854 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:15855 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:35317632 (33.6 MB)  TX bytes:1917434 (1.8 MB) 
          Interrupt:20  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 

Note: 
How do I know what's My proxy IP address & Proxy Port? 
ales how do I opne this file on terminal command: 
/etc/clamav/freshclam.conf 
By adding the following Information 
---->[COLOR=red]HTTPProxyServer[/COLOR] 
---->[COLOR=red]HTTPProxyPort [/COLOR] 
 
Thank you for you help

---

### Post by ~sHyLoCk~ on 2009-09-22
Do you use proxy? if not leave them.
Try ```
sudo gedit /etc/clamav/freshclam.conf
```

---

