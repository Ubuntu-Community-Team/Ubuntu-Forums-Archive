---
title: "Need help with loading ICS script at startup..."
date: 2009-06-12
forum: General Help
---

### Post by pro003 on 2009-06-12
Ok. I have managed to share my internet connection on wlan0 i.e ppp0 to eth0 internal network so that laptop with vista *(my wife's) should have internet too. Now the problem am facing is that after every reboot I have to manually execute the script, which is btw:

```
#!/bin/bash
INTIF="eth0"
EXTIF="ppp0"
EXTIP="`/sbin/ifconfig ppp0 | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`"
/sbin/depmod -a
/sbin/modprobe ip_tables
/sbin/modprobe ip_conntrack
/sbin/modprobe ip_conntrack_ftp
/sbin/modprobe ip_conntrack_irc
/sbin/modprobe iptable_nat
/sbin/modprobe ip_nat_ftp
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "1" > /proc/sys/net/ipv4/ip_dynaddr
iptables -P INPUT ACCEPT
iptables -F INPUT 
iptables -P OUTPUT ACCEPT
iptables -F OUTPUT 
iptables -P FORWARD DROP
iptables -F FORWARD 
iptables -t nat -F
iptables -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
iptables -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE 
```

and just adding it at startup apps doesn't solve the problem, I still need to execute it manually. I even added "sleep 40 &&" right below the #!/bin/bash, and that didn't work either.

Any ideas?

Thanks.

---

### Post by blueridgedog on 2009-06-12
Is it possible that your wireless lan is not "up" until you log in and it can access your key ring?  If you have some type of access control on your wireless, then the script will fail.  

If it was a normal interface, I would edit /etc/init.d/rc.local as root with:

```
gksudo gedit /etc/init.d/rc.local 
```

Add a line at the very end of the file that calls the full path to your script.

```
/the/full/path/to/your/firewallscript
```

However, I don't think in this case your wireless link is up until you log in.

---

### Post by jimv on 2009-06-12
You could install Firestarter and use that to setup ICS.  Make sure to install the dhcp3-server package too, then open Firestarter, go to Edit>Preferences>Network Settings and check "Enable Internet Connection Sharing" and "Enable DHCP Server for Local Network".

---

### Post by pro003 on 2009-06-12
a. BlueridgeDog! You're the man! Thanx like 1,000x 4this1!!!


b. Jimv, thank you too. I've tried using firestarter to share internet but couldn't make it some errors were poppin'up, nevertheless, thanks. 

c. this thread [SOLVED]

---

