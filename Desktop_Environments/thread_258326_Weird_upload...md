---
title: "Weird upload.."
date: 2006-09-15
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-09-15
I have some weird upload sometimes, it's always 42bit and it appears like every second.. I have no idea which app is causing this and I don't know how to identify it.
I checked my system with chkrootkit and rkhunter and both didn't find anything.
Anyone an idea on how I can identify where this weird upload comes from??

---

### Post by OffHand on 2006-09-15
Type this in the terminal to get a list of internet connections...
```
netstat --tcp --udp
```

---

### Post by Ramses de Norre on 2006-09-16
The problem is that it doesn't seem listed in netstat.. I'll look for it again the next time the upload appears.

---

### Post by Ramses de Norre on 2006-09-16
This is the only output of the netstat command: ```
ramses@icarus:~$ netstat --tcp --udp
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost:48945         localhost:46519         ESTABLISHED
tcp        0      0 localhost:46519         localhost:48945         ESTABLISHED
ramses@icarus:~$

```

And I have a periodic small network activity on athO (my wireless nic).
It appears like every two seconds and for the moment it's upload and a bit download..

---

### Post by ayoli on 2006-09-16
try ```
netstat -atupe
``` that shoud give more info
btw, it could be simple communication between your wireless interface and the access point.

---

### Post by Ramses de Norre on 2006-09-16
This is the output with all internet applications closed:```
ramses@icarus:~$ sudo netstat -atupe
Password:
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode      PID/Program name
tcp        0      0 localhost:55555         *:*                     LISTEN     root       25754      31521/avgscan
tcp        0      0 *:10024                 *:*                     LISTEN     root       28267      653/apache
tcp        0      0 localhost:mysql         *:*                     LISTEN     root       27115      32439/mysqld
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     root       27980      381/smbd
tcp        0      0 *:x11                   *:*                     LISTEN     root       24799      31011/X
tcp        0      0 localhost:48945         *:*                     LISTEN     hplip      24871      31101/hpiod
tcp        0      0 localhost:7634          *:*                     LISTEN     root       27025      32356/hddtemp
tcp        0      0 *:ssh                   *:*                     LISTEN     root       27926      413/sshd
tcp        0      0 localhost:ipp           *:*                     LISTEN     root       30191      1272/cupsd
tcp        0      0 *:smtp                  *:*                     LISTEN     root       27542      32737/master
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     root       27979      381/smbd
tcp        0      0 localhost:41694         *:*                     LISTEN     hplip      24916      31164/python
tcp        0      0 localhost:48945         localhost:46519         ESTABLISHEDhplip      24874      31101/hpiod
tcp        0      0 localhost:46519         localhost:48945         ESTABLISHEDhplip      24922      31164/python
tcp        0      0 icarus:42706            72.14.221.104:www       TIME_WAIT  root       0          -
tcp        0      0 localhost:7634          localhost:33511         TIME_WAIT  root       0          -
tcp        0      0 icarus:42288            72.14.221.147:www       TIME_WAIT  root       0          -
tcp        0      0 icarus:42290            72.14.221.147:www       TIME_WAIT  root       0          -
tcp        0      0 icarus:40551            66.102.9.147:www        TIME_WAIT  root       0          -
udp        0      0 *:32769                 *:*                                avahi      26532      31866/avahi-daemon:
udp        0      0 icarus:netbios-ns       *:*                                root       27852      355/nmbd
udp        0      0 *:netbios-ns            *:*                                root       27849      355/nmbd
udp        0      0 icarus:netbios-dgm      *:*                                root       27853      355/nmbd
udp        0      0 *:netbios-dgm           *:*                                root       27850      355/nmbd
udp        0      0 *:5353                  *:*                                avahi      26531      31866/avahi-daemon:
ramses@icarus:~$ nslookup 72.14.221.104
Server:         195.130.131.1
Address:        195.130.131.1#53

** server can't find 104.221.14.72.in-addr.arpa: NXDOMAIN

ramses@icarus:~$ nslookup 66.102.9.147
Server:         195.130.131.1
Address:        195.130.131.1#53

** server can't find 147.9.102.66.in-addr.arpa: NXDOMAIN

ramses@icarus:~$
```
And what I think is strange are those connections from root, as you can see I can't lookup their dns and I have no idea where they come from.
There is also no connection to my acces point it seems which is at 192.168.123.254.
Oh and I am running apache on port 10024 and I've blocked the two IPs from the root connections and the strange up/download behavior seems to have changed. But not disappeard.

---

### Post by ayoli on 2006-09-16
theseroot connections with these 2 foreign ips are in TIME_WAIT so we can't see what app they use, you should run the netstat a the right moment, maybe with a script in a loop or with [multitail]("http://www.vanheusden.com/multitail/") (i renember that i used it to monitor my ethernet activity with netstat running in when i was paranoiac)

---

### Post by Ramses de Norre on 2006-09-16
Could postfix be causing this? I found this:```
tcp        0      1 icarus:55601            gsmtp183.google.co:smtp SYN_SENT   postfix    99460      30147/smtp
tcp        0      1 icarus:55602            gsmtp183.google.co:smtp SYN_SENT   postfix    99461      30148/smtp
tcp        0      1 icarus:34898            gsmtp163.google.co:smtp SYN_SENT   postfix    99462      30149/smtp
tcp        0      1 icarus:34895            gsmtp163.google.co:smtp SYN_SENT   postfix    99459      30146/smtp
tcp        0      1 icarus:34894            gsmtp163.google.co:smtp SYN_SENT   postfix    99458      29794/smtp
```
It's configured to send system mail to gmail acount so that could also be an explanation though I didn't get mail..

And I blocked the two strange IPs and they're gone but the traffic remains..

I also found IPs in the same range of the two strange ones (they only have a different last number) that came from my regular user and from firefox.

---

### Post by ayoli on 2006-09-16
the only thing that comes to my mind at the moment is that you ve choosed the right topic, that's *weird*.#-o

---

### Post by Ramses de Norre on 2006-10-02
I think I have found what caused this upload, I disabled a remote cifs mount (I think mount tried to reach the host the whole time when he was offline, which caused continious traffic) and I disabled forwarding system mail to a gmail address, I think something was misconfigured there but I don't need it anyway.
It seems most of the strange traffic (I hope allà has disappeard.
Lets hope it doesn't come back =)

---

