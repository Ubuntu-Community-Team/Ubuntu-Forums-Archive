---
title: "Of WoW and iptables..."
date: 2006-08-22
forum: Gaming &amp; Leisure
---

### Post by toasterofirony on 2006-08-22
For my piece of mind, I introduced iptables into the mix following [this guide]("http://doc.gwos.org/index.php/IptablesFirewall"). The problem arose when I tried to play WoW (via Wine). It refused to start. Or rather it claimed to have started when I looked in the sys resource monitor, but it wasn't on the desktop. Now WoW was working fine last check and sure enough when I stopped the iptables it worked again.

So I introduced a rule as per the suggestions given in the guide to allow WoW   to access the internet, via the port given on the WoW site:

```
#Allow WoW
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 3724 -j ACCEPT
```

But this doesn't seem to have sorted my problem. I'm not entirely sure what I'm doing, so if anyone could explain to me anything I'm missing I'd appreciate it.

---

