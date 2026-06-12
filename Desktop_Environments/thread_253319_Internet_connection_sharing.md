---
title: "Internet connection sharing"
date: 2006-09-08
forum: Desktop Environments
---

### Post by jrev on 2006-09-08
In order to activate Internet sharing over 3 PC's on Dapper I have made a script named S95.sh placed in the folder /etc/rcS.d 
Here it is :

# partagez votre connexion internet. fichier à placer à la fin du dossier /etc/rcS.d

#!/bin/sh
iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -o ppp0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

file proprieties are : root.root 755 as the other files *.sh of the same folder
If I type this script lines by hand the sharing don't work either

Can you imagine what prevent this internet connection sharing ?

It worked fine with Breezy 

Thanks everybody with a good hint

---

### Post by tuxinvader on 2006-09-08
You need to have some rules in your FORWARD chain in the filter table too.

Try adding:

iptables -P FORWARD DROP
iptables -A FORWARD -s 192.168.0.0/24 -j ACCEPT
iptables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -j LOG --log-prefix "Drop Fwd "

---

### Post by jrev on 2006-09-09
Is there a good tuto on the english wiki on that subject ?

I don't quite understand your answer 

In which file should I add these lines ?

Thanks anyway

---

### Post by jrev on 2006-09-13
Thanks for your attention. The answer is :

Install firestarter and configure it 

a couple of minutes is enough

Bye for now 

Why make it simple when we can make it difficult ?
Cause it's my way

---

