---
title: "Maple 9.5 hang problem network related"
date: 2005-10-31
forum: Desktop Environments
---

### Post by bmcage on 2005-10-31
Hi, 

I installed Maple 9.5 on Kubuntu, but should be the same for Ubuntu. However, Maple only works when I'm not connected to the network. Here is the problem: 

1/I installed maple 9.5 single user from the CD. This must be done in konsole with "sh install". I did it as root. Beter not to this it appears as you then need to do chgrp to the user that will use Maple, and chmod g+w to get the required permissions.  However, maple now works.

2/This is on a laptop, and I connect wirelessly to the net. All is fine, I connect to the AP. Then I type "dhclient" to get an IP, and hey, now Maple 9.5 does not work anymore. (luckely you can print, just not execute any commands). If you kill maple, and all children processes, you cannot start a new maple, it just hangs on the splash screen.

3/Maple works with TCP/IP ports, as they say here [http://www.maplesoft.com/support/faqs/Maple95/Installation/2.aspx](http://www.maplesoft.com/support/faqs/Maple95/Installation/2.aspx)
However Maple 9.5 works just fine on my PC with Mandrake 10.1, fixed connection, so the firewall should not be messing it up. 

Anybody an idea what could be going on? An Ubuntu problem, or something with the router, .... :confused:

---

### Post by FizDev on 2005-12-15
This might be a little late but I've also installed Maple 9.5 and I can tell you that it works perfectly on my laptop with Breezy Badger. So I guess that your problem is your router. Personnally, I have a Linksys WRT54G router and Maple doesn't seems to have any problems. Maybe if you try a fresh install!?
I just hope this helps you. :???:

I believe it might be also related to the fact that you've installed Maple as root.

---

