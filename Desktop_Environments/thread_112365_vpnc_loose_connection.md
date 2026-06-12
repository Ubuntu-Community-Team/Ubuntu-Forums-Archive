---
title: "vpnc loose connection"
date: 2006-01-04
forum: Desktop Environments
---

### Post by kajko on 2006-01-04
Hi.
I run vpnc using command:
           sudo vpnc --enable-1des
After set connection I am able to work 5-20 minutes then vpnc froze. Looks like all out coming Internet is out. I am not able to browse any page, but I am able to listen the Internet radio.  
To solve this problem I have to restart vpnc.
          sudo vpnc-disconnect
and then connect again.
I am keep on one terminal a ping to one of ours internal computer then connection is longer. When I was not using ping the time of vpnc connection was less then 5min.

Please help me to solve this problem?
Ubuntu 5.10
Thank you.
Mariusz

---

### Post by kajko on 2006-01-04
Hi
I try debug it
I run: 
 sudo vpnc --enable-1des --debug 2 --no-detach

I receive:
......
sending packet: len = 100, padding = 2
sending packet: len = 100, padding = 2
sending packet: len = 100, padding = 2
sending packet: len = 91, padding = 3
sending packet: len = 100, padding = 2
sending packet: len = 100, padding = 2
sending packet: len = 100, padding = 2
sending packet: len = 100, padding = 2
sending packet: len = 100, padding = 2
sending packet: len = 100, padding = 2
sending packet: len = 100, padding = 2
sending packet: len = 100, padding = 2

Those line was all time just diffrent len and padding numbers but it was running all time. Mintime I loose connection. I connect to our server and this was last what I was able to do. 
When I try disconnect vpnc I receive:

sending packet: len = 91, padding = 3
sending packet: len = 100, padding = 2
sending packet: len = 100, padding = 2
sending packet: len = 100, padding = 2
sending packet: len = 100, padding = 2
sending packet: len = 100, padding = 2
sending packet: len = 100, padding = 2
sending packet: len = 100, padding = 2
sending packet: len = 100, padding = 2
[3]   Killed                  sudo vpnc --enable-1des

[4]+  Stopped                 sudo vpnc --enable-1des --debug 2 --no-detach
kajko@gruzy:~$ sudo vpnc-disconnect
Password:
no vpnc found running
kajko@gruzy:~$ ps -A|grep vpnc
15076 pts/3    00:00:01 vpnc
kajko@gruzy:~$ sudo kill -9 15076
kajko@gruzy:~$ 

Why vpnc-disconnect didn't find a running vpnc?
How I can find more information which will help to solve this problem.
Thank you for help
Mariusz

---

