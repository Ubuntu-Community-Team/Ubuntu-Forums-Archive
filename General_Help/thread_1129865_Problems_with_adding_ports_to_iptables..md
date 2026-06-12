---
title: "Problems with adding ports to iptables."
date: 2009-04-19
forum: General Help
---

### Post by cherva on 2009-04-19
Can someone help me figure out the command to add a port opening in iptables ? When I add port 22 to firestarter it adds the port in the INBOUND table but if I add the prort with ```
iptables -A INBOUND -p tcp --dport 22 -j ACCEPT
``` it adds it ,but the port is not opened.

---

### Post by lovinglinux on 2009-04-19
The **[color=#FF0000]INBOUND[/color]** chain is not a default chain. It is created by Firestarter to handle complex filtering tasks. So if you are trying to add a new iptables rules without starting Firestarter, then it will not work.

You should use this rule instead if you are not running Firestarter first:

```
iptables -A[color=#FF0000]** INPUT **[/color]-p tcp --dport 22 -j ACCEPT
```

If you are using Firestarter and just want to add the[color=#FF0000] **INBOUND**[/color] rule by command line, then you should change the position of the rule. If Firestarter already configured the iptables, your new rule will placed in the bottom of the chain and will not work, because there is probably a DROP condition before it dropping all packages.

I recommend reading these:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by cherva on 2009-04-19
Thanks

---

