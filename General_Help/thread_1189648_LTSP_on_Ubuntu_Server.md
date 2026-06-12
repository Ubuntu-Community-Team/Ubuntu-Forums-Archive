---
title: "LTSP on Ubuntu Server"
date: 2009-06-16
forum: General Help
---

### Post by Textstar on 2009-06-16
I am running a Ubuntu Server I plan to use as an LTSP server behind an IPcop firewall. IPcop handles all DHCP, DNS, Intrusion Detection etc....I just found out about LTSP and I think I could use something like this. I have noticed a lot of tutorials suggest using 2 nic cards on the machine running LTSP (In my case the Ubuntu server) and my question is should I have 2 nic cards even if I have IPcop running 2 nics?. It says that one of the cards would be connected to the router (IPcop). IPcop is connected in from the  DSL box and out to the switch. Do I need to go out from IPcop to the LTSP Server and then out to the switch? Secondly will this App Server LTSP serve Windows applications to Windows machines as well as Ubuntu apps to Ubuntu machines.My network has 3 Win XP machines ,2 Ubuntu desktops 1 Ubuntu Server total. I hope this question has not been asked already

---

### Post by Aearenda on 2009-06-17
> ...should I have 2 nic cards even if I have IPcop running 2 nics?. It says that one of the cards would be connected to the router (IPcop). IPcop is connected in from the DSL box and out to the switch. Do I need to go out from IPcop to the LTSP Server and then out to the switch? 
LTSP should be downstream from IPCOP. However, the terminal computers boot using PXE and this needs specific DHCP and DNS settings. These are done for you in a 2-nic LTSP setup, with the terminals downstream of the LTSP server. If you want IPCop to provide the appropriate settings, it can be done but will require some manual setup. I recommend you experiment with a trial setup first to gain experience before committing yourself.

> Secondly will this App Server LTSP serve Windows applications to Windows machines as well as Ubuntu apps to Ubuntu machines.My network has 3 Win XP machines ,2 Ubuntu desktops 1 Ubuntu Server total.
No it won't, at least not like a Windows Terminal Server could. LTSP is designed to run with low-power terminals, which start up with a Linux kernel over the net and then log the user on to a session on the server. So LTSP serves sessions, not applications. You can run Windows apps in WINE in the sessions, with care.
The Ubuntu clients could use the LTSP server remotely using XDMCP (direct from GDM or by xnest or Xephyr) but this isn't really what LTSP is all about.

I'll dig out a link with more detail and edit this post with it.
EDIT: Try these:
[https://help.ubuntu.com/community/EdubuntuFAQ](https://help.ubuntu.com/community/EdubuntuFAQ)
[http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/ltsp-theory.html](http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/ltsp-theory.html)
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)
[https://help.ubuntu.com/community/EdubuntuDocumentation/EdubuntuCookbook/ThinClient](https://help.ubuntu.com/community/EdubuntuDocumentation/EdubuntuCookbook/ThinClient)

---

