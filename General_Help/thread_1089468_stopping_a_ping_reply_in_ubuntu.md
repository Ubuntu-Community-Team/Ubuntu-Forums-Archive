---
title: "stopping a ping reply in ubuntu"
date: 2009-03-07
forum: General Help
---

### Post by grubster on 2009-03-07
I keep failing a port scan with shields up. My computer keeps replying to a ping request. Can it be stopped so i am completely invisible on the internet?

---

### Post by Xiong Chiamiov on 2009-03-07
Take a look at [UFW](https://wiki.ubuntu.com/UbuntuFirewall).  I don't know what the default firewall settings are in Ubuntu, I'm pretty sure you can block pings with iptables, which UFW uses.

---

### Post by albandy on 2009-03-07
sudo su -c "echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all"

---

### Post by grubster on 2009-03-07
If i run this code in terminal can i change this back if it doesnt work?

---

### Post by albandy on 2009-03-07
yes, simply change 1 to 0, or restart the computer

---

### Post by grubster on 2009-03-07
tried another scan but it failed. I keep replying to a ping. Also im using shields up.

---

### Post by albandy on 2009-03-07
see this screenshot

---

### Post by grubster on 2009-03-07
cheers mate for your help.

---

### Post by ssam on 2009-03-07
there is no harm in replying to a ping.

if you dont reply, an attacker still knows that your are there, if you weren't there they would get a 'no route to host' or 'Destination Host Unreachable'. or see [http://kb.nitix.com/1756](http://kb.nitix.com/1756) for more info

---

