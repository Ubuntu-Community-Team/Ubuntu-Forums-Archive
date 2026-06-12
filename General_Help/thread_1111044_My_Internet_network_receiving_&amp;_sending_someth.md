---
title: "My Internet network receiving &amp; sending something!!"
date: 2009-03-30
forum: General Help
---

### Post by AlNaimi on 2009-03-30
Hi every one
As i said before, My Internet network show me a signal, The system monitor show in Network history that over 20 mg receiving with 11 kb/s
also sending 20 MG with 11 kb/s.
I do nothing right now, NO uploading + No downloading
What is going on?
Any body help me with this situation, I'm also a bignneer.
Thanks In advanced

---

### Post by heindsight on 2009-03-30
If you open a terminal and run the following command it will show all active network connections:
```
sudo netstat -tuaevpn
```

If you post the output of that command here, I'm sure someone will be able to help you figure out what's going on.

---

### Post by change_mode on 2009-03-30
You can also install Wireshark and capture the traffic.

---

### Post by AlNaimi on 2009-03-30
Thanks guys
Right now it is:
Receiving: 110 MG 16Kb/s
Sending: 90 MG 16kb/s
And this is the activity:
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode       PID/Program name
tcp        0      0 127.0.0.1:32000         0.0.0.0:*               LISTEN      1000       16434       5638/java       
tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN      112        14967       5110/privoxy    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      0          14896       5065/cupsd      
tcp        0      0 192.168.2.100:34072     74.125.113.102:80       ESTABLISHED 0          99535       7617/firefox    
tcp        0      0 127.0.0.1:32000         127.0.0.1:31000         ESTABLISHED 1000       16603       5625/wrapper-linux-
tcp6       0      0 ::1:9481                :::*                    LISTEN      1000       19053       5638/java       
tcp6       0      0 127.0.0.1:9481          :::*                    LISTEN      1000       19052       5638/java       
tcp6       0      0 ::1:8888                :::*                    LISTEN      1000       16683       5638/java       
tcp6       0      0 127.0.0.1:8888          :::*                    LISTEN      1000       16682       5638/java       
tcp6       0      0 fe80::21f:3cff:fe3:8058 :::*                    LISTEN      1000       19062       5638/java       
tcp6       0      0 127.0.0.1:31000         127.0.0.1:32000         ESTABLISHED 1000       16602       5638/java       
udp        0      0 0.0.0.0:68              0.0.0.0:*                           0          20100       6142/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           110        14815       5017/avahi-daemon: 
udp        0      0 0.0.0.0:42990           0.0.0.0:*                           110        14816       5017/avahi-daemon: 
udp6       0      0 :::21131                :::*                                1000       18926       5638/java       
udp6       0      0 :::8008                 :::*                                1000       19074       5638/java       
udp6       0      0 :::1993                 :::*                                1000       18925       5638/java       
udp6       0      0 :::1900                 :::*                                1000       19067       5638/java       
>>>>>>>>>>>>>>>>>>>>>>>>>>>>
i will try to download the program ...
but if you can show me which program is using the internet behind me?
thanks agin

---

### Post by AlNaimi on 2009-03-30
And also how could i run Wireshark?

---

### Post by change_mode on 2009-03-30
sudo wireshark (it needs su access to capture the data)

> tcp 0 0 192.168.2.100:34072 74.125.113.102:80 ESTABLISHED 0 99535 7617/firefox

That's the only active internet connection shown there and it's google.com... that wouldn't cause constant traffic.
Every 10 minutes or so, Firefox downloads a malware/phishing blocklist from google, could that be it?

---

### Post by AlNaimi on 2009-03-30
Thanks Change-Mode ....
I still could not know which program is doing that and how to stop it..
Plz help me i don't want to go back to Windows
this my activeity after stoping firefox:
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode       PID/Program name
tcp        0      0 127.0.0.1:32000         0.0.0.0:*               LISTEN      1000       16434       5638/java       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      0          14896       5065/cupsd      
tcp        0      0 192.168.2.100:42682     82.103.134.102:80       TIME_WAIT   0          0           -               
tcp        0      0 192.168.2.100:55609     91.189.94.12:80         TIME_WAIT   0          0           -               
tcp        0      0 192.168.2.100:42691     82.103.134.102:80       TIME_WAIT   0          0           -               
tcp        0      0 192.168.2.100:42123     72.21.207.112:80        TIME_WAIT   0          0           -               
tcp        0      0 192.168.2.100:42685     82.103.134.102:80       TIME_WAIT   0          0           -               
tcp        0      0 127.0.0.1:32000         127.0.0.1:31000         ESTABLISHED 1000       16603       5625/wrapper-linux-
tcp        0      0 192.168.2.100:42684     82.103.134.102:80       TIME_WAIT   0          0           -               
tcp        0      0 192.168.2.100:42681     82.103.134.102:80       TIME_WAIT   0          0           -               
tcp        0      0 192.168.2.100:41524     67.210.118.45:80        TIME_WAIT   0          0           -               
tcp6       0      0 ::1:9481                :::*                    LISTEN      1000       19053       5638/java       
tcp6       0      0 127.0.0.1:9481          :::*                    LISTEN      1000       19052       5638/java       
tcp6       0      0 ::1:8888                :::*                    LISTEN      1000       16683       5638/java       
tcp6       0      0 127.0.0.1:8888          :::*                    LISTEN      1000       16682       5638/java       
tcp6       0      0 fe80::21f:3cff:fe3:8058 :::*                    LISTEN      1000       19062       5638/java       
tcp6       0      0 127.0.0.1:31000         127.0.0.1:32000         ESTABLISHED 1000       16602       5638/java       
udp        0      0 0.0.0.0:68              0.0.0.0:*                           0          124949      19707/dhclient  
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           110        14815       5017/avahi-daemon: 
udp        0      0 0.0.0.0:42990           0.0.0.0:*                           110        14816       5017/avahi-daemon: 
udp6       0      0 :::21131                :::*                                1000       18926       5638/java       
udp6       0      0 :::8008                 :::*                                1000       19074       5638/java       
udp6       0      0 :::1993                 :::*                                1000       18925       5638/java       
udp6       0      0 :::1900                 :::*                                1000       19067       5638/java 
and the wireless signal still blinking and the trafic still go on.

---

### Post by kpatz on 2009-03-30
You can use tcpdump - it's simpler than wireshark.

Some of those entries are connections to Canonical servers - typically this is the update manager checking for updates.

You will also see ARP traffic - which is computers and routers asking machines to identify themselves (MAC address->IP address and back).  If there are a lot of computers on your network, you will see correspondingly more ARP traffic.

---

### Post by DGortze380 on 2009-03-30
There are no connections on that list that look malicious.

If you are connected to a network, you will (in most cases) send and receive traffic constantly. There are a number of reasons, such as arp requests, routing protocol updates, netbios (if you have a windows box on the system).

There does appear to be anything to worry about, it's most likely normal network overhead.

---

### Post by AlNaimi on 2009-03-30
Thanks alot guys
And i hope every things going OK
And i want to ask you about,how i can restore ubuntu Or rebuild it again and get it fresh again like first time?
Thanks again

---

### Post by DGortze380 on 2009-03-30
> **AlNaimi said:**
> Thanks alot guys
And i hope every things going OK
And i want to ask you about,how i can restore ubuntu Or rebuild it again and get it fresh again like first time?
Thanks again

Just reinstall. Same as the first time you installed it.

---

