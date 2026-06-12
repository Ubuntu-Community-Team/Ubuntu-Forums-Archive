---
title: "Using sudo for running applications -- please help."
date: 2005-07-11
forum: Desktop Environments
---

### Post by kagashe on 2005-07-11
Hi,

I have successfully installed Ubuntu 5.04 on my Laptop.

For connecting to internet I am using CDMA mobile instrument which works as a wireless modem (connected through USB port).

The mobile operator provided Dialer software in tar.gz files which I have downloaded and installed as an executable program called "RConnect".

When I run command "RConnect" there is an internet connection through ppp0 interphase which I can confirm "as working" through the Network Monitor.

When I start any Internet application whether it be Evolution, Firefox or Gaim, I can't access the internet, e.g. in Firefox I get an alert "http://" could not be found please check the name and try again.

When I start all these applications through sudo (sudo firefox) I can access the internet.

I have checked the "user priviledges" and they are all ticked. In fact I have created only one user who has all the priviledges including sudo.

I have checked Firefox configuration both for sudo as well as without sudo by typing about:config in the browser and could not find any difference.

It is interesting to note that for running "RConnect" program I don't have to use sudo. Only point to note is, this program has not been installed through apt-get or Synaptic Package Manager but directly running its install.sh.

I had also posted similar post in "Networking" forum but could not get proper responce. Since it is posted under "Hardware" I am posting this here once again.

I am familiar with Linux to some extent. Infact, I have Mandrakelinux 10 running on the same machine (with dual boot) where I connect to internet through same "RConnect" program and open Firefox, Evolution etc without root priviledges.

kagashe

---

### Post by magoo on 2005-07-11
Can you please produce the ouput of the following commands when it is working:
```

$ ifconfig ppp0 # or the name of the device created by the script
$ netstat -nr

```?
Thanks in advance

---

### Post by kagashe on 2005-07-11
> vidya2@ubuntu:~$ ifconfig ppp0 #
ppp0      Link encap:Point-to-Point Protocol
          inet addr:220.226.17.212  P-t-P:97.237.2.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:264  Metric:1
          RX packets:517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:497 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:118188 (115.4 KiB)  TX bytes:32508 (31.7 KiB)

vidya2@ubuntu:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
97.237.2.5      0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
0.0.0.0         97.237.2.5      0.0.0.0         UG        0 0          0 ppp0
vidya2@ubuntu:~$


kagashe

---

### Post by magoo on 2005-07-11
should have asked this before:

and the DNS?
$cat /etc/resolve.conf

and what is the output of pinging google
$ ping [www.google.com](www.google.com)

---

### Post by kagashe on 2005-07-11
I am posting the earlier ones also:
> vidya2@ubuntu:~$ ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol
          inet addr:220.226.57.24  P-t-P:97.237.2.16  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:264  Metric:1
          RX packets:683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:627 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:139922 (136.6 KiB)  TX bytes:51569 (50.3 KiB)

vidya2@ubuntu:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
97.237.2.16     0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
0.0.0.0         97.237.2.16     0.0.0.0         UG        0 0          0 ppp0

There is no file resolve.conf, I think you mean resolv.conf
> 
vidya2@ubuntu:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: Permission denied
vidya2@ubuntu:~$ sudo cat /etc/resolv.conf
nameserver 202.138.103.100
nameserver 202.138.96.2
nameserver 202.138.103.100
nameserver 202.138.96.2
vidya2@ubuntu:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
vidya2@ubuntu:~$ sudo ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (64.233.189.104) 56(84) bytes of data.
64 bytes from 64.233.189.104: icmp_seq=1 ttl=248 time=802 ms
64 bytes from 64.233.189.104: icmp_seq=2 ttl=248 time=699 ms
64 bytes from 64.233.189.104: icmp_seq=3 ttl=248 time=579 ms
64 bytes from 64.233.189.104: icmp_seq=4 ttl=248 time=659 ms
64 bytes from 64.233.189.104: icmp_seq=5 ttl=248 time=587 ms
64 bytes from 64.233.189.104: icmp_seq=6 ttl=248 time=668 ms
64 bytes from 64.233.189.104: icmp_seq=7 ttl=248 time=478 ms
64 bytes from 64.233.189.104: icmp_seq=8 ttl=248 time=676 ms
64 bytes from 64.233.189.104: icmp_seq=9 ttl=248 time=611 ms
64 bytes from 64.233.189.104: icmp_seq=10 ttl=248 time=575 ms
64 bytes from 64.233.189.104: icmp_seq=11 ttl=248 time=556 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
11 packets transmitted, 11 received, 0% packet loss, time 10963ms
rtt min/avg/max/mdev = 478.827/627.028/802.479/82.472 ms
vidya2@ubuntu:~$
I had to add sudo to cat resolv.conf
Please note that I could not ping also, unless I type sudo ping, which proves my point that there is internet access with sudo only.

kagashe

---

### Post by magoo on 2005-07-11
[QUOTE=kagashe]
I had to add sudo to cat resolv.conf
[/QUOTE]
Your normal users are not able to resolve DNS names.

My /etc/resolv.conf:
```

magnus@minix:~$ ls -la /etc/resolv.conf
-rw-r--r--  1 root root 67 2005-07-11 21:08 /etc/resolv.conf
magnus@minix:~$

```
is readable by all users.

I think the script calls pppd which is suid root (explains that you don't need to sudo Rconnect), but the resolv.conf file has wrong permissions.

Chmoding the file will, I think, solve the problem
```

$ sudo chmod 644 /etc/resolv.conf

```

This "error" can be in the script or in the wrong options passed to pppd.

I can't help you more than that without knowing what the rconnect is in detail.

---

### Post by kagashe on 2005-07-11
[QUOTE=magoo]Your normal users are not able to resolve DNS names.

My /etc/resolv.conf:
```

magnus@minix:~$ ls -la /etc/resolv.conf
-rw-r--r--  1 root root 67 2005-07-11 21:08 /etc/resolv.conf
magnus@minix:~$

```
is readable by all users.

I think the script calls pppd which is suid root (explains that you don't need to sudo Rconnect), but the resolv.conf file has wrong permissions.

Chmoding the file will, I think, solve the problem
```

$ sudo chmod 644 /etc/resolv.conf

```

This "error" can be in the script or in the wrong options passed to pppd.

I can't help you more than that without knowing what the rconnect is in detail.[/QUOTE]

Problem solved by changing the permission as suggested by you. Thank you very much. Offcourse, I can tell you about RConnect. It is downloaded from:
[http://www.relianceinfo.com/Infocomm/Rim/rconnect_dc_linux.html](http://www.relianceinfo.com/Infocomm/Rim/rconnect_dc_linux.html)
The web page says that it is meant for Redhat 8.0. I am using it for any Linux distribution just by modifying its config file so that it points to correct device e.g. /dev/ttyACM0 in case of Ubuntu and /dev/usb/acm/0 in case of Mandrakelinux 10.

I would be greatful if you tell me how to solve the following problem also.

When I connect the mobile phone to USB port for the first time it gets linked to /dev/ttyACM0. The RConnect config file has a link for /dev/ttyACM0 and it connects. Suppose I plug out the USB connection due to some reason and "plug it in" in the same port the machine detects as if it is another device and allots /dev/ttyACM1 and the RConnect script fails. Moreover, if I change the RConnect config file to point to the new link /dev/ttyACM1, then also it fails to connect. I have to reboot the machine to connect once again.

How do I tell the machine that it is the same device without restarting?

kagashe

---

### Post by kagashe on 2005-07-12
> Problem solved by changing the permission as suggested by you.
When I restarted the permision of /etc/resolv.conf was required to be changed once again.

Does it mean that RConnect is rewriting the file every time?

or sytem is rewriting the file when I restart?

which one?

kagashe

---

### Post by magoo on 2005-07-12
[QUOTE=kagashe]When I restarted the permision of /etc/resolv.conf was required to be changed once again.

Does it mean that RConnect is rewriting the file every time?

or sytem is rewriting the file when I restart?

which one?
[/QUOTE]

I would say both. Are the permission wrong before you are connected? 
The resolv.conf file is rewritten each time you connect by the pppd daemon with the information it receives from your ISP. 
I think the umask is wrong when starting the rconnect. Have you changed the umask settings?

mine is 
```

magnus@minix:~$ umask -p
umask 0022
magnus@minix:~$ umask -S
u=rwx,g=rx,o=rx
magnus@minix:~$

```

I think you can add a line in the rconnect script diong it each time but I agree it is not the best solution.

Concerning your hotplug issue, I always try to stand farther away possible from hotplug stuff :-) but if it happens that you disconnect the modem, simply first try to ```
 $ rdisconnect
```
then check if ppp0 has disappeared (ifconfig ppp0) if yes wait some seconds and plug your modem again and rconnect again. (check ```
$ tail -f /var/log/messages
``` to see the deallocation of the device corresponding to the modem).
If ppp0 is still there you need to kill the pppd daemon (I assume it is the *only* ppp connection you have!). shoot ```
$ sudo killall pppd
``` and check again for the presence of ppp0.

---

### Post by kagashe on 2005-07-12
> I would say both. Are the permission wrong before you are connected?
Yes. I looked at the messages on the screen before gnome login appears. The file resolv.conf is getting modified (I think because it does not find any ppp interphase).

I was using rdisconnect and killall pppd earlier also. Anyway the problem has disappeared now.

Thanks for your help.

kagashe

---

