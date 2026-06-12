---
title: "Iptables woes:"
date: 2006-01-04
forum: General Help
---

### Post by klepto on 2006-01-04
Ok.. I am a new comer to the ubuntu movement. 
I am running Kubuntu Breezy and I've got everything running pretty well
with a compaq m2105us laptop. I've been pulling my hair out with
iptables because when i want to turn off my firewall and use a bittorrent
client it shutsdown my network all together.

i do a: iptables -F and iptables -X
then /etc/init.d/networking restart

even with no firewall running bittorrent on ubuntu doesn't seem to
work well with my linksys router. The ports are open on the router
but do I have to forward the packets?

Any input is appreciated!

---

### Post by Pawel Stolowski on 2006-01-04
You don't need to restart networking - it is enough to just clear firewall rules with iptables -F and iptables -X. Depending on the iptables rules you use, you may also need to reset firewall policy (e.g. iptables -P INPUT ACCEPT; iptables -P OUTPUT ACCEPT).

As on bittorrent... Yes, you need to forward bittorrent ports to your ubuntu PC on your linksys router. See you the router manual on how to do this.

---

