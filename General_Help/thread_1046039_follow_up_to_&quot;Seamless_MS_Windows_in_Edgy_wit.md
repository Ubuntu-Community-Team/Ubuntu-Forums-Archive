---
title: "follow up to &quot;Seamless MS Windows in Edgy with VirtualBox and Beryl!&quot;"
date: 2009-01-21
forum: General Help
---

### Post by rupert on 2009-01-21
Hello,
i am following howto below.
However we get everything running, but I cant ping the VM from the Host where it is running, strangely we can ping the VM from a different PC in our subnet.

this is my rc.local
<code>
tunctl -t tap0 -u he
chmod 0666 /dev/net/tun
/usr/sbin/brctl addbr br0
/sbin/ifconfig eth0 0.0.0.0 promisc
/usr/sbin/brctl addif br0 eth0
/sbin/dhclient br0
/usr/sbin/brctl addif br0 tap0
ifconfig tap0 192.168.50.217 netmask 255.255.252.0 up
bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
route add -host 192.168.50.32 dev tap0
arp -Ds 192.168.50.32 eth0 pub

</code>

the VM has the IP 192.168.50.46, which we cant ping from the localhost

hope someone is still on this

thx

---

