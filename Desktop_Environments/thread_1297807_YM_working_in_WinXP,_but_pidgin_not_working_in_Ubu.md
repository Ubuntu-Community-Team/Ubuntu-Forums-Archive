---
title: "YM working in WinXP, but pidgin not working in Ubuntu on same PC"
date: 2009-10-22
forum: Desktop Environments
---

### Post by smecherel on 2009-10-22
Hello, 
I'm using Ubuntu 9.04 and WinXP on the same machine (not the same time - dual boot), with the same private IP configuration on both sistems. I'm behind a CheckPoint Firewall which i do not administer.
The problem i have is that Messenger in Windows is working, and Pidgin in Ubuntu is not working. Since i'm not really a beginner, here's what is happening, perhaps some of you guys can help me with this.


AAA. On windowsXP. ####################################
1. Yahoo Messenger 9.0.0.2162 -> Preferences -> Connections -> Connect via a proxy server -> HTTP Proxy (if any) in IE
2. Internet Explorer -> Internet Options -> Connections -> LAN Setting -> No Proxy Servers
Basically im connecting directly to yahoo server on port 80.
Here is how the communication works with help of wireshark:

Step 1. 
- DNS query for httpvcs1.msg.yahoo.com
- DNS replay with canonical name httpcs1.msg.vip.sp2.yahoo.com -> 216.155.194.34
- 3 way handshake with 216.155.194.34:80
- My pc send GET /capacity
- My pc receives CP_IP_ADDRESS=216.155.194.248
- FIN - ending session

Step 2.
- DNS query for httpvcs2.msg.yahoo.com
- DNS replay with canonical name httpcs1.msg.vip.ac4.yahoo.com -> 98.136.112.56
- 3 way handshake with 98.136.112.56:80
- My pc send GET /capacity
- My pc receives CP_IP_ADDRESS=98.136.113.169
- FIN - ending session

Step 3.
- 3 way handshake with 98.136.113.169:443
- Some Hellos, key exchange etc,
- FIN - ending session

Step 4 - (probably the authentification).
- DNS query for login.yahoo.com
- DNS replay with 217.12.8.76
- 3 way handshake with 217.12.8.76:443
- Some data exchange
- FIN - ending session

Step 5. 
- 3 way handshake with 98.136.113.169:80
- from now on many tcp pachets exchanged, the messenger is succesfully conencted.

I repeated the connection again, and the only thing that is changed is on Step2 where CP_IP_ADDRESS returned from httpvcs2.msg.yahoo.com is not anymore 98.136.113.169 but is 98.136.112.218. And of course, this IP is changed in the folowing steps from 98.136.113.169 to 98.136.112.218
#######################################
#######################################
BBB. On Ubuntu 9.04.###################
Pidgin 2.5.5 is installed via: sudo apt-get install pidgin
When creating the account, it has the folowing 3 important settings besides Protocol (YahooMesenger) and user/pass:
PAGE SERVER: scsa.msg.yahoo.com
PAGE PORT: 5050
PROXY TYPE: GNOME PROXY SETTINGS

Step 1. If i try to connect pidgin with the default settings this happends in wireshark:
- DNS query for scsa.msg.yahoo.com
- DNS replay with 68.180.217.15
- It tryes 3 way handshake with 68.180.217.15:5050 but only the first packet with SYN bit is send, no sys/ack received back - i'm preaty sure that the firewall is blocking 5050.

Step 2. So i have changed the PAGE PORT to 80. Now:
- DNS query for scsa.msg.yahoo.com
- DNS replay with 68.180.217.15
- 3 way handshake with 68.180.217.15:80
- The next packet is sent from my PC on port 80, is some HTTP data
- The replay to that packet from 68.180.217.15 is a packet with RST bit set, so the connection is closed.

Step 3. The same behavior is if i change the PROXY TYPE to NO PROXY

Step 4. I tryed another thing. I have modified the PAGE SERVER with httpvcs1.msg.yahoo.com and also with 98.136.113.169 - taken from windows connection sniffing (see AAA. On windowsXP). Then:
- DNS query for scsa.msg.yahoo.com
- DNS replay with 68.180.217.15
- 3 way handshake with httpvcs1.msg.yahoo.com:80 or 98.136.113.169:80
- The next packet is sent from my PC on port 80, is some HTTP data
- My pc receives an Acknowledgement replay from httpvcs1.msg.yahoo.com:80 or 98.136.113.169:80 and then nothing hapends the connections just stays active no further packets exchange.
#######################################
So as you can see, the communication that Yahoo Messenger has with the Yahoo server on windows, is very different that the pidgin has on Linux. I fear the worst, that pidgin is not written to be able to connect to yahoo behind a firewall.
If there is on this forum a sparckling mind to know what am i missing, i would be really thankfull.

If you read until now, thanks for having the time and curiosity.

---

