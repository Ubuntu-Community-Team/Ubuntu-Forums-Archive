---
title: "no wlan with kernel 2.6.15-26"
date: 2006-09-03
forum: Desktop Environments
---

### Post by sonium on 2006-09-03
Hi, I'm currently using kernel 2.6.15-25-686 and so far everything works fine. But if I boot kernel 2.6.15-26-686 my wlan interface (D-Link DWL650+ acx100) doesn't show up. I also have installed -26-686-restricted-modules.

lsmod shows me that the acx module is loaded as in the working kernel.

---

### Post by sonium on 2006-09-03
I found out that it works again after doing

sudo rmmod acx
sudo modprobe acx

but I have to do this again after every reboot

---

### Post by Eversmann on 2006-09-03
Maybe you just need to load the module everytime you reboot.

Try to add it to /etc/modules and see how it goes.

---

### Post by sonium on 2006-09-03
I will try it, but the problem is not that it wouldn't load but it loaded and not working or recogniced.

I also found out, that it there is something wrong with iptables just after reloading the module.
for example ping says:
*ping: sendmsg: operation not permitted*

So I have to flush the tables to make it working again:

sonium@raumstation:~$ sudo iptables -P INPUT ACCEPT
sonium@raumstation:~$ sudo iptables -P FORWARD ACCEPT
sonium@raumstation:~$ sudo iptables -P OUTPUT ACCEPT
sonium@raumstation:~$ sudo iptables -F

---

