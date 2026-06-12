---
title: "Debian Unable to Setup Network &amp; Unable to connect to internet"
date: 2018-06-04
forum: Debian
---

### Post by skyluke.1987 on 2018-06-04
Dear all, I would need some advice on the following: 

1. SELKS 4.0 desktop.
2. Installed on physical server.
3. /etc/network/interface (File settings)
   > auto lo
      iface lo inet loopback
      
      iface eno1 inet static 
      address 10.0.106.61
      netmask 255.255.255.0
      network 10.0.106.0
      broadcast 10.0. 106.255
      gateway 10.0.106.1
4. sudo vim /etc/resolv.conf (Settings with nameservers)

When I run ifup eno1, RTNETLINK answers: File exists, ifup: failed to bring up eno1.
"Network not configured" error displayed.  
Run "ifconfig" only displaying one network which is "lo"

Run "cd /etc/network  >> ls"
- eno1
- eno2
- eno3 
- eno4
- lo

Run "cd /etc/network >> ls"
- if-down.d
- if-post-down.d
- if-pre-up.d
- if-up.d
- interfaces
- interfaces.d

Restarted network settings: service networking restart

..... After performing all the above, including a system reboot, there is still no network on the machine. Kindly advise.

---

### Post by TheFu on 2018-06-05
Welcome to the forums.

18.04 doesn't use the interfaces file.  Netplan is used now.
resolv.conf is managed by the resolvconf package, not manually since 12.04.

So, to start, we need to know which release you are using and which network devices are on your machine and where those devices are connected.

Let's start with these commands. Please show your work and please, please, please use "code tags" so the output lines up correctly.

```
sudo lshw -C network
ifconfig
route -n
```

I have no idea about debian versioning/releases and how that alters network configs.  That isn't ubuntu.

---

### Post by slickymaster on 2018-06-05
Thread moved to **Debian** for a better fit

---

### Post by skyluke.1987 on 2018-06-05
> [COLOR=#000000][FONT=&amp]sudo lshw -C network[/FONT][/COLOR] 
Command not found. 

> route -n 
Empty - no record

Which part should I also check? As all the IP addresses are working on the other partition on Windows Server setting.

---

### Post by TheFu on 2018-06-06
No route. That would be bad on any Linux. 

Frustrating when questions aren't answered.

---

### Post by skyluke.1987 on 2018-06-07
Hi, could it be some settings which are not done properly during the installation phase? Not possible to change after it? 

Do I need to reinstall it to be a better option? So far seems like no one have solution to it. :(

---

### Post by TheFu on 2018-06-07
If questions aren't answered, how can we help?

---

### Post by arochester on 2018-06-10
Selks is **based on** Debian.

Would it not be more appropriate on Forum: Ubuntu/Debian BASED >>> [https://ubuntuforums.org/forumdisplay.php?f=452](https://ubuntuforums.org/forumdisplay.php?f=452)

---

