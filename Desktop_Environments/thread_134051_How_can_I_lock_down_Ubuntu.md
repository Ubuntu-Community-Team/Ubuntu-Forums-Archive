---
title: "How can I lock down Ubuntu"
date: 2006-02-21
forum: Desktop Environments
---

### Post by karlharratt on 2006-02-21
I have been asked to set up an Internet cafe on a very small budget, I am planning to use an ADSL / NAT router issuing DHCP, an Ubuntu server with Squid (or similar web proxy) and DansGuardian (content control).
For clients I am planning Ubuntu desktop PC's but would like to lock down the desktop so that all they have is Firefox (via the proxy) and Evolution Mail (via either sendmail or web based e-mail).
Also is there a way to auto-configure Evolution to pick up mail depending upon which user is logged on to the computer.

---

### Post by nkhansen on 2006-02-21
[QUOTE=karlharratt]I have been asked to set up an Internet cafe on a very small budget, I am planning to use an ADSL / NAT router issuing DHCP, an Ubuntu server with Squid (or similar web proxy) and DansGuardian (content control).
For clients I am planning Ubuntu desktop PC's but would like to lock down the desktop so that all they have is Firefox (via the proxy) and Evolution Mail (via either sendmail or web based e-mail).[/QUOTE]

What is your timeframe? In GNOME 2.14, there will be a relatively easy lockdown editor. Other than that, you could check out 
[http://gnomelockdown.sourceforge.net/quickstart.php](http://gnomelockdown.sourceforge.net/quickstart.php)


[QUOTE=karlharratt]Also is there a way to auto-configure Evolution to pick up mail depending upon which user is logged on to the computer.[/QUOTE]
Isn't Evolution configuration based on who is logged on? All of my Evolution-configuration is in my home directory.

---

