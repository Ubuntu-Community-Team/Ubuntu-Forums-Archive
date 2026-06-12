---
title: "flash, firefox needing ports for gui?"
date: 2009-01-22
forum: General Help
---

### Post by dakun on 2009-01-22
ive been messing around with iptables for a couple of weeks now and ive ran into a few issues.  with my restrictions active, firefoxes user interfaces slows down noticably, as well as flash. flash seems to be a worse case becuase when i right click on it, everything freezes but my mouse and it seems to ignore anything i do. i can still restart x using the hotkeys though.

ipTablesConf.py reads portlist for the list of ports that i want left open

heres the scripts ive been using for the time being:
portlist
```
80
443
1863
5050
5190
5222
6667

```

ipTablesConf.py
```

import os

#obtains port list
fIn = open("/home/dakun/programming/python/ipTableConf/portList","r")
portList = fIn.readlines()

#removes \n from then of lines
portList = [port[:len(port)-1] for port in portList]

#ensures a fresh iptables list
os.system("sudo iptables -F")
os.system("sudo iptables -P INPUT DROP")
os.system("sudo iptables -P FORWARD DROP")
os.system("sudo iptables -P OUTPUT DROP")

#allows ports for output
for port in portList:
    os.system("sudo iptables -A OUTPUT -p tcp --dport "+port+" -j ACCEPT")

#allows in and out from router
os.system("sudo iptables -A INPUT -p udp -s 192.168.0.1 -d 0/0 -j ACCEPT")
os.system("sudo iptables -A OUTPUT -p udp --dport 53 --sport 1024:65535 -j ACCEPT")

#allows all related and established connections from output for input
os.system("sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -p tcp -j ACCEPT")

#outputs the list if ran manually to lib notify
if os.path.exists("list.py"):
    os.system("sudo python list.py")

```

---

### Post by dakun on 2009-03-25
when blocking ports in iptables, remember to allow LO for in and out

sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A OUTPUT -o lo -j ACCEPT

---

