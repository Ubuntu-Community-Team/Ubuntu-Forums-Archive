---
title: "vpnc gui"
date: 2005-11-26
forum: Desktop Environments
---

### Post by windowsXuser on 2005-11-26
I made a post about this in my other thread and for some reason it doesn't show the post anymore.  I was confused about it, so decided to make another thread.

I was having problems with vpnc and getting it to connect to my school.  I downloaded it through the terminal and couldn't seem to find where it was getting installed so i could edit the vpnc.conf file to config it for the host.

I tried using kvpnc with vpnc, but i kept getting errors with it.  Does anyone know of a nice gui to use with vpnc?  I am trying to connect through cisco if that helps at all.

let me know.
blair..

---

### Post by bin on 2005-11-26
[http://ubuntuforums.org/showthread.php?t=21054&page=6](http://ubuntuforums.org/showthread.php?t=21054&page=6)

To be honest, kvpnc is about the best gui there is for vpnc!!!

However, it's time for you to provide a little more info.
1. How do you connect to net - modem or router
2. Have you been able to connect to your school vpn from windows, if so, were you using a Cisco vpn client.
3. Which vpn server is being used on the Cisco box at the school
4. Depending on the answers to som eof the above, do you have a cisco .pcf file which wil contain the config needed to connect
5. When reporting errors or problems with linux of any sort, do not just say you keep getting errors - please list actions and responses/results. Folks will always help if they can, but maximum input is needed from you - and if it's any help I've been trying for ages to connect to my cisco at work via linux and am struggling - it depends very much on how the server is set up.

in light

bin

---

### Post by windowsXuser on 2005-11-26
[QUOTE=bin][http://ubuntuforums.org/showthread.php?t=21054&page=6](http://ubuntuforums.org/showthread.php?t=21054&page=6)

To be honest, kvpnc is about the best gui there is for vpnc!!!

However, it's time for you to provide a little more info.
1. How do you connect to net - modem or router
2. Have you been able to connect to your school vpn from windows, if so, were you using a Cisco vpn client.
3. Which vpn server is being used on the Cisco box at the school
4. Depending on the answers to som eof the above, do you have a cisco .pcf file which wil contain the config needed to connect
5. When reporting errors or problems with linux of any sort, do not just say you keep getting errors - please list actions and responses/results. Folks will always help if they can, but maximum input is needed from you - and if it's any help I've been trying for ages to connect to my cisco at work via linux and am struggling - it depends very much on how the server is set up.

in light

bin[/QUOTE]


hey,

1. I connect to the internet through a router
2. I have been able to connect to my school using windows and a VPN Cisco client.
3. I have no clue which vpn server is being used on the Cisco box at my school
4.  I dont have a cisco .pcf file, i was just going to have a vpnc.conf file with the following:
IPSec gateway vpn.algonquincollege.com
IPSec ID VPNGroup1
IPSec secret VPNGroup1
Xauth username <cotn0016>

I guess i need a cisco.pcf file too?

blair..

---

### Post by windowsXuser on 2005-11-26
ok.. i finally got the vpnc to connect to my school.

i just made a new .conf file in my vpn directory.

IPSec gateway vpn.algonquincollege.com
IPSec ID VPNGroup1
IPSec secret VPNGroup1
Xauth username cotn0016

then in the terminal:
root@kubuntu:~# sudo vpnc /etc/vpnc/myFile.conf

entered my network password and received this mssg.
connect Banner:
| Algonquin College VPN Service
|
| Please visit [http://www.algonquincollege.com/its/support/connecthome](http://www.algonquincollege.com/its/support/connecthome) to ensure you have an updated client.

VPNC started in background (pid: 9176)...

thanks for all your help..

---

