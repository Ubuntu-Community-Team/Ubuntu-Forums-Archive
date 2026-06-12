---
title: "Problem with Apache Logs"
date: 2010-09-07
forum: Desktop Environments
---

### Post by khatkarrohit on 2010-09-07
Hi
I have installed apache web-server on Ubuntu 10.04. I use uTorrent and qbittorrent. These two software creates so many entries in apache log like these:

domain.com:80 127.0.0.1 - - [07/Sep/2010:12:06:49 +0530] "GET /announce?info_hash=%8e%bc%f4%c5%60%60%80%21%b2TD~%02%87Zr%7b%04%b1g&peer_id=-UT2040-RT%97%120%eey%cb6%5b%d3%f5&port=48681&uploaded=59293696&downloaded=0&left=0&corrupt=0&key=FEDE6EB2&event=started&numwant=200&compact=1&no_peer_id=1 HTTP/1.1" 301 930 "-" "uTorrent/2040(21586)"
domain.com:80 127.0.0.1 - - [07/Sep/2010:12:06:49 +0530] "GET /announce/?info_hash=%8e%bc%f4%c5%60%60%80%21%b2TD~%02%87Zr%7b%04%b1g&peer_id=-UT2040-RT%97%120%eey%cb6%5b%d3%f5&port=48681&uploaded=59293696&downloaded=0&left=0&corrupt=0&key=FEDE6EB2&event=started&numwant=200&compact=1&no_peer_id=1 HTTP/1.1" 200 605 "-" "uTorrent/2040(21586)"
domain.com:80 127.0.0.1 - - [07/Sep/2010:12:06:50 +0530] "GET /announce?info_hash=%8e%bc%f4%c5%60%60%80%21%b2TD~%02%87Zr%7b%04%b1g&peer_id=-UT2040-RT%97%120%eey%cb6%5b%d3%f5&port=48681&uploaded=59293696&downloaded=0&left=0&corrupt=0&key=FEDE6EB2&event=started&numwant=200&compact=1&no_peer_id=1 HTTP/1.1" 301 913 "-" "uTorrent/2040(21586)"
domain.com:80 127.0.0.1 - - [07/Sep/2010:12:06:50 +0530] "GET /announce/?info_hash=%8e%bc%f4%c5%60%60%80%21%b2TD~%02%87Zr%7b%04%b1g&peer_id=-UT2040-RT%97%120%eey%cb6%5b%d3%f5&port=48681&uploaded=59293696&downloaded=0&left=0&corrupt=0&key=FEDE6EB2&event=started&numwant=200&compact=1&no_peer_id=1 HTTP/1.1" 200 599 "-" "uTorrent/2040(21586)"
domain.com:80 127.0.0.1 - - [07/Sep/2010:12:11:07 +0530] "GET /scrape?info_hash=%91%7c%9a%5b9%f1%9c%bbl%d1%ed%2fz%7b%b2%8d%ca%1e%8b%8f HTTP/1.1" 301 645 "-" "uTorrent/2040(21586)"
domain.com:80 127.0.0.1 - - [07/Sep/2010:12:11:07 +0530] "GET /scrape/?info_hash=%91%7c%9a%5b9%f1%9c%bbl%d1%ed%2fz%7b%b2%8d%ca%1e%8b%8f HTTP/1.1" 200 602 "-" "uTorrent/2040(21586)"
domain.com:80 127.0.0.1 - - [07/Sep/2010:12:11:08 +0530] "GET /scrape?info_hash=%91%7c%9a%5b9%f1%9c%bbl%d1%ed%2fz%7b%b2%8d%ca%1e%8b%8f HTTP/1.1" 301 645 "-" "uTorrent/2040(21586)"
domain.com:80 127.0.0.1 - - [07/Sep/2010:12:11:08 +0530] "GET /scrape/?info_hash=%91%7c%9a%5b9%f1%9c%bbl%d1%ed%2fz%7b%b2%8d%ca%1e%8b%8f HTTP/1.1" 200 603 "-" "uTorrent/2040(21586)"


I want these log entries not to be logged in apache logs from these bittorrent clients. Please Tell me how to remove these entries and thanks in advance.

---

### Post by khatkarrohit on 2010-10-04
I have removed my Desktop from DMZ and used port forwarding.

But no solution.

I have some more information about this.

i ran this command sudo netstat -tulpn
and see what i got. qBittorrent uses the 6771 port but it was given 6881 port.


udp        0      0 192.168.1.2:6771        0.0.0.0:*                           3173/qbittorrent
udp        0      0 127.0.0.1:6771          0.0.0.0:*                           3173/qbittorrent
udp        0      0 0.0.0.0:6771            0.0.0.0:*                           3173/qbittorrent


If I ran uTorrent then it also uses the 6771 port simultaneously. Look at this:

udp        0      0 0.0.0.0:6771            0.0.0.0:*                           3918/utorrent.exe
udp        0      0 192.168.1.2:6771        0.0.0.0:*                           3173/qbittorrent
udp        0      0 127.0.0.1:6771          0.0.0.0:*                           3173/qbittorrent
udp        0      0 0.0.0.0:6771            0.0.0.0:*                           3173/qbittorrent


I guess the log entries that are coming in apache logs is simple broadcast.
Now see this the event logs from FireStarter:
Time:Oct  4 17:23:41 Direction: Unknown In:eth0 Out: Port:6771 Source:192.168.1.2 Destination:239.192.152.143 Length:146 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct  4 17:23:41 Direction: Unknown In:eth0 Out: Port:6771 Source:192.168.1.2 Destination:239.192.152.143 Length:146 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct  4 17:23:41 Direction: Unknown In:eth0 Out: Port:6771 Source:192.168.1.2 Destination:239.192.152.143 Length:146 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct  4 17:23:41 Direction: Unknown In:eth0 Out: Port:6771 Source:192.168.1.2 Destination:239.192.152.143 Length:146 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct  4 17:23:41 Direction: Unknown In:eth0 Out: Port:6771 Source:192.168.1.2 Destination:239.192.152.143 Length:146 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct  4 17:23:41 Direction: Unknown In:eth0 Out: Port:6771 Source:192.168.1.2 Destination:239.192.152.143 Length:146 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct  4 17:23:41 Direction: Unknown In:eth0 Out: Port:6771 Source:192.168.1.2 Destination:239.192.152.143 Length:146 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct  4 17:23:41 Direction: Unknown In:eth0 Out: Port:6771 Source:192.168.1.2 Destination:239.192.152.143 Length:146 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct  4 17:23:42 Direction: Unknown In:eth0 Out: Port:6771 Source:192.168.1.2 Destination:239.192.152.143 Length:146 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct  4 17:23:42 Direction: Unknown In:eth0 Out: Port:6771 Source:192.168.1.2 Destination:239.192.152.143 Length:146 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct  4 17:23:42 Direction: Unknown In:eth0 Out: Port:6771 Source:192.168.1.2 Destination:239.192.152.143 Length:146 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct  4 17:23:43 Direction: Unknown In:eth0 Out: Port:6771 Source:192.168.1.2 Destination:239.192.152.143 Length:146 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct  4 17:23:43 Direction: Unknown In:eth0 Out: Port:6771 Source:192.168.1.2 Destination:239.192.152.143 Length:146 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct  4 17:23:43 Direction: Unknown In:eth0 Out: Port:6771 Source:192.168.1.2 Destination:239.192.152.143 Length:146 TOS:0x00 Protocol:UDP Service:Unknown
Time:Oct  4 17:23:45 Direction: Unknown In:eth0 Out: Port:1900 Source:192.168.1.2 Destination:239.255.255.250 Length:128 TOS:0x00 Protocol:UDP Service:SSDP
Time:Oct  4 17:23:53 Direction: Unknown In:eth0 Out: Port:1900 Source:192.168.1.2 Destination:239.255.255.250 Length:128 TOS:0x00 Protocol:UDP Service:SSDP
Time:Oct  4 17:24:03 Direction: Unknown In:eth0 Out: Port:1900 Source:192.168.1.2 Destination:239.255.255.250 Length:128 TOS:0x00 Protocol:UDP Service:SSDP

Later I installed OpenTracker
and the interesting part is that because of these logs tracker in uTorrent shows the PirateBay tracker live and no of Peers is same as of the OpenTracker at localhost.

Now I am assure that its the Bittorrent protocol that is using the broadcast or some miss configuration of apache. **Only the default host is getting these type of pings or logs not any other virtual host.**

Very wiered things are happening in my PC.
There is some ghost in my PC......lloll

---

### Post by khatkarrohit on 2010-10-04
I want help with Apache.

Can anybody share the apache configuration file here.

File 1 : **httpd.conf**

File 2: any virtual host file in **sites-enabled** directory.

---

