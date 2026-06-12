---
title: "Cant connect to localhost"
date: 2006-01-14
forum: Desktop Environments
---

### Post by %hMa@?b&lt;C on 2006-01-14
I have been completely confused by this.  I cannot ping localhost, i cannot SSh, i cannot connect to the CUPS server, or even print, I cannot telnet, I cannot use PuTTY or anything that requires connection to localhost.  Any help would be appreciated

---

### Post by schilcha on 2006-01-14
try "ifconfig" to see, if there's a device called "lo" set up. If not, try "sudo ifup lo". 

Also, have a look at the file /etc/network/interfaces. In mine, the first lines look like this: 
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


---

### Post by dcstar on 2006-01-14
[QUOTE=jeffc313]I have been completely confused by this.  I cannot ping localhost, i cannot SSh, i cannot connect to the CUPS server, or even print, I cannot telnet, I cannot use PuTTY or anything that requires connection to localhost.  Any help would be appreciated[/QUOTE]
Tell us the following:

Contents of /etc/hosts file;

Results of: "netstat -rn", "hostname"

---

### Post by Mr_Grieves on 2006-01-14
As I've helped you abit on the way before I can say that he is not using any iptable rules..

Paste the output of you routing tabling

```

netstat -r

```

---

### Post by %hMa@?b&lt;C on 2006-01-14
```

crowell@ubuntu:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.9.34.1       *               255.255.255.255 UH        0 0          0 ppp0
default         10.9.34.1       0.0.0.0         UG        0 0          0 ppp0
crowell@ubuntu:~$


```

---

### Post by Mr_Grieves on 2006-01-14
You have no route to the local host.. I think..

route -n

What does that give?

---

### Post by Mr_Grieves on 2006-01-14
```

sudo ifconfig lo localhost
sudo route add localhost dev lo

```

Does that help?

---

### Post by %hMa@?b&lt;C on 2006-01-14
[QUOTE=Mr_Grieves]```

sudo ifconfig lo localhost
sudo route add localhost dev lo

```

Does that help?[/QUOTE]
Thank you so much!

---

### Post by Mr_Grieves on 2006-01-14
Ahh. Atlast :)

---

### Post by kenzie on 2008-01-30
> **Mr_Grieves said:**
> ```

sudo ifconfig lo localhost
sudo route add localhost dev lo

```


Can anyone tell me how to make this permanent? Right now when I reboot this fix is lost. I'm on Ubuntu 7.10 and a VPS. Thanks!

---

