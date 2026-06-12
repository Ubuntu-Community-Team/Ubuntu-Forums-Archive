---
title: "Can't connect to the internet after power outage."
date: 2006-04-11
forum: Desktop Environments
---

### Post by javi0084 on 2006-04-11
The power went out in my house for about 5 seconds and after that I can't connect to the internet using Ubuntu but my Windows machine still connects without a problem. Both workstations are connected to the same switch and both show a green light. I am new to Linux and any help will be appreciated.

Thanks, javi.

---

### Post by kingmonkey on 2006-04-11
Can you ping the ubuntu machine from windows?

---

### Post by stozball on 2006-04-11
If your ubuntu workstation able to get an IP address from your router?

Open up a terminal (Applications > Accessories > Terminal) and type ifconfig

Look for your ethernet interface in the output and see what it says for "inet addr"

---

### Post by localzuk on 2006-04-11
Have you tried rebooting the computer? Also, have you tried disabling and re-enabling the network card via the Networking control panel? Are you sure it is not the router? ie. Is it a dhcp server also and if it is, is it still serving IP addresses. To check this, on the Windows box, open a command prompt (Start > Run > cmd) and type 'ipconfig /renew-all'

---

### Post by javi0084 on 2006-04-11
I rebooted the computer and it does get an IP and my router assigned one but I can't ping it from Windows and I can't ping anything from Ubuntu, it tells me that the network is unreachable. I aslo disabled/enabled the NIC but that didn't make a difference.

---

### Post by stozball on 2006-04-11
Do you have any free ports on the switch? Could you try moving your ubuntu machine from one port on the switch to another one?

Also, to see if the problem is with your ubuntu configuration or your hardware you could try booting up from a live CD.

Edit: Sometimes switches, particually cheap desktop switches, have trouble when they first turn on after a power outage. I've seen a couple of different brands where I've had to power them off an on again to get them to work properly. You could try this also.

---

### Post by chrisjs162216 on 2006-04-16
Grr...accidently pressed the back button instead of posting, so I have to start over.  OK, in a terminal, type 'nano /etc/resolv.conf'
Delete any text listed, and use the dns nameservers you're WinXP computer uses (Control Panel, click Network Connections, right click the connection it uses, click Status, click Support tab, click Details... and look for 'DNS Servers'  There should be 2 IP addresses listed, and write down the first one listed.  Then on your Ubuntu machine, under /etc/resolv.conf type 'nameserver 000.000.000.000' where 000.000.000.000 is the IP address you wrote down from your windows machine.  For example, mine is 'nameserver 68.87.73.242'  

Then restart networking.  In terminal, type '/etc/init.d/networking restart'

Then try pinging google ('ping -c 4 google.com')

If it works, congrats, otherwise, I dunno what's up with it

---

