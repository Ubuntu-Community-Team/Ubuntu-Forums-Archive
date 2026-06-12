---
title: "Can't ssh from one host to another since changing from Wifi to LAN connection"
date: 2011-08-25
forum: Desktop Environments
---

### Post by juliushibert63 on 2011-08-25
I can't connect to a Ubuntu 10.04 machine via ssh unless I'm on my local network. 

I've tried turning off my firewall (through Firestarter) which I would have thought would be causing the problem but not such luck. The problem has only just started occurring after switching my connection from Wifi to a LAN cable via an AV Power Plug LAN Adapter. 

So here's my basic setup Host 1 (Ubuntu 10.04 machine that I'm trying to ssh into). This only accepts connections on a non default port number and only from IPs in my local network 192.168.0.1 - 192.168.0.254. Host 2 (DD-WRT router which I connect to first to then connect to Host 1) this accepts connections on the usual ssh port from the outside world. 

When I'm on my macbook on Wifi I'm able to connect to Host 1 via ssh as per normal. However when I try to connect from the outside world (as I would have done previously when Host 1 was connected to the internet by Wifi and not LAN) I can get a connection to Host 2 fine. But once I try to connect from Host 2 to Host 1 (ie from the DD-WRT router to the Ubuntu 10.04 machine) I get the following error

```
root@DD-WRT:~# ssh gil@192.168.0.42 -p 55831
ssh: connection to gil@192.168.0.42:55831 exited: remote closed the connection
```

Anyone know why I can't seem to connect to Host 1 via ssh when connecting through Host 2?

---

### Post by juliushibert63 on 2011-08-31
After spending a lot of time digging around online and through the various config files it looks like hosts.deny is causing the problem as there's the following line at the end 

```
sshd: 192.168.0.129
```

I'm guessing this is blocking logins from the first ssh host.

The problem now is everything I use nano to edit /etc/hosts.deny to remove that line, within about 5seconds the /etc/hosts.deny file default back to having sshd: 192.168.0.129 right at the end of the file. No matter what I do I can't seem to get rid of it from that file which is very very frustrating.

---

### Post by juliushibert63 on 2011-09-01
In case anyone else is having this problem I managed to suss it out after a lot of hard work.

Turns out it was Deny Hosts that was blocking me out because there'd been three failed password attempts from the router. 

Here's the solution as quoted from the DenyHosts FAQ page.

How can I remove an IP address that DenyHosts blocked?


> If you have been accidentally locked out of one of your hosts (because DenyHosts has added it to /etc/hosts.deny you may have noticed that simply removing it from /etc/hosts.deny does not in itself correct the issue) since DenyHosts keeps track of the attempts in the WORK_DIR files. In order to cleanse the address you will need to do the following:
Stop DenyHosts
Remove the IP address from /etc/hosts.deny
Edit WORK_DIR/hosts and remove the lines containing the IP address. Save the file.
Edit WORK_DIR/hosts-restricted and remove the lines containing the IP address. Save the file.
Edit WORK_DIR/hosts-root and remove the lines containing the IP address. Save the file.
Edit WORK_DIR/hosts-valid and remove the lines containing the IP address. Save the file.
Edit WORK_DIR/user-hosts and remove the lines containing the IP address. Save the file.
(optional) Consider adding the IP address to WORK_DIR/allowed-hosts
Start DenyHosts
Note: Not all of the WORK_DIR files will contain the IP address so you may want to use grep to determine which files contain the IP address.


Source: [http://denyhosts.sourceforge.net/faq.html#3_20](http://denyhosts.sourceforge.net/faq.html#3_20)

---

