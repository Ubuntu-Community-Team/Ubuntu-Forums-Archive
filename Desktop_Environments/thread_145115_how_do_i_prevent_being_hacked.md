---
title: "how do i prevent being hacked?"
date: 2006-03-15
forum: Desktop Environments
---

### Post by risknothin on 2006-03-15
my buddy thinks he can get into my system how can i make sure he doesnt?

---

### Post by KingBahamut on 2006-03-15
apt-get install firestarter 

configure firestarter to disallow all incoming traffic from his IP address.

---

### Post by risknothin on 2006-03-15
yeah i have firestarter but he thinks he can get past that

is that true?

---

### Post by kaamos on 2006-03-15
Accessing any machine is very easy if you have physical access. Some steps to make that more difficult:
- use a BIOS password
- set the HD as first (and only) in the BIOS boot order
- password protect grub [[link](http://tinyurl.com/n3w7n)]
- and if you want real protection, re-install the os with ecryted partitions [[link](http://ubuntuforums.org/showthread.php?t=120091)]

The last one is probably the only real protection as the BIOS passwd can often be changed pretty easily. (like removing the battery perhaps?)

---

### Post by KingBahamut on 2006-03-15
iptables -A INPUT -s x.x.x.x -j DROP

where x is the IP address of your offending Address, this would be for an iptables/netfilter rule. 

But as far as him being able to buffer overflow on it, it might be possible to vulner iptables , which is what I believe firestarter is using as its base. But hed probably need a bigger pipe than yours to do it. 

Just an opinion.

---

### Post by stabface on 2006-03-15
what type of hacking are you talking about? is he on the same network? the same room? what os is he using?

---

### Post by risknothin on 2006-03-15
hes using ubuntu and he knows my ip address but after that i dont know what he is doing. He just said that it is going to try and get in.

---

### Post by KingBahamut on 2006-03-15
Is your IP address private or public? 

Are you on the same network or not? 

Are you on the same ISP network?

---

### Post by risknothin on 2006-03-15
he knows my ip i dont know if it is public or private but he wrote it down when i wasnt paying attention.  we both are on the same isp.

---

### Post by Azrael on 2006-03-15
[quote=KingBahamut]iptables -A INPUT -s x.x.x.x -j DROP

where x is the IP address of your offending Address, this would be for an iptables/netfilter rule. 

But as far as him being able to buffer overflow on it, it might be possible to vulner iptables , which is what I believe firestarter is using as its base. But hed probably need a bigger pipe than yours to do it. 

Just an opinion.[/quote] Filtering a single source address is no good. An attacker can easily use a different IP address.

Also, I find it very unlikely that you'll find a buffer overflow vulnerability in iptables. I'm quite sure a high profile app like iptables is already *pretty* thorougly tested anded ironed out by now.

I think a default Ubuntu install is reasonably secure against remote attacks. A nessus scan on my own Ubuntu box didn't show any significant weak points anyway.

---

### Post by KingBahamut on 2006-03-15
apt-get install arping. 

Usage -- [http://www.habets.pp.se/synscan/programs.php](http://www.habets.pp.se/synscan/programs.php)

Arping to the address and get the MAC, then block the MAC. 

iptables -A MACtest -m mac --mac-source 00:11:22:33:44:55 -j DROP

were the 00:11:22:33:44:55 , is the mac address your blocking.

---

### Post by Azrael on 2006-03-15
[quote=KingBahamut]apt-get install arping. 

Usage -- [http://www.habets.pp.se/synscan/programs.php]("http://www.habets.pp.se/synscan/programs.php")

Arping to the address and get the MAC, then block the MAC. 

iptables -A MACtest -m mac --mac-source 00:11:22:33:44:55 -j DROP

were the 00:11:22:33:44:55 , is the mac address your blocking.[/quote]
I know you're just trying to help, but that's even flimsier advice there...

For instance:

sudo apt-get install macchanger
sudo macchanger -m  00:00:DE:AD:BE:EF ethX

Besides, who says the attacker will launch his attack from his own box?

---

