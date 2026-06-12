---
title: "firewall question with frostwire."
date: 2009-05-16
forum: General Help
---

### Post by ontherooftop on 2009-05-16
I have opened and forwarded port 36014 in my router, but frostwire says
I am still behind a firewall, I know there is a default firewall on in ubuntu but I am wondering is there a program that can allow the ubuntu firewall to give full permission to frostwire or allow both udp and tcp 
connections to port 36014, Thanks.

---

### Post by lovinglinux on 2009-05-16
If you didn't setup the firewall (iptables) then all ports are open, because all connections are allowed by default. 

I don't know how Frostwire checks for the open port, but maybe the address used by the program to scan the port is down or not accessible.

Alternatively, you can test by visiting [http://www.pcflank.com/scanner1.htm](http://www.pcflank.com/scanner1.htm) and scan the port selected. If the results tells you that the port is "Stealth" then it's not open and you might have an issue on the router port forwarding. Check if you have forwarded the port to the correct internal IP of your machine.

If you still want to setup the firewall, then I recommend using gufw. It is called "Firewall Configuration" in the "Add/Remove" manager.

---

### Post by ontherooftop on 2009-05-16
thanks, would you recommend gaurd dog firewall?

---

### Post by lovinglinux on 2009-05-16
> **ontherooftop said:**
> thanks, would you recommend gaurd dog firewall?
I tried it when I was starting to use Ubuntu, but never went too far with it. I think gufw is much more simple and easy to configure.

If you want something more complex and powerful, then you should try learning how to create your own iptables rules, without a firewall manager like ufw or guard dog.

Recommended iptables reading:

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)
[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

With gufw you don't have to learn the iptables commands, because the application creates the rules for you.

---

