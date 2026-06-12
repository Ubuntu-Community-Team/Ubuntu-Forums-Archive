---
title: "Open Sim Grids &amp; Configuring Ports"
date: 2011-05-27
forum: Gaming &amp; Leisure
---

### Post by FernandoTertiary on 2011-05-27
Hola,
Am just getting setup with OpenSim Grid & a couple independent Grids for the Metaverse Virtual Reality realm & am having Server problems within Port recognition. When attempting to begin the Grid Server instance, there is a error pertaining the ports not being recognizable. When doing a nmap test, the results are:

```
nmap -sU -sT -P0 192.168.0.25 -p 9000
Starting Nmap 5.21 ( http://nmap.org ) at 2011-05-27 12:30 EET
mass_dns: warning: Unable to determine any DNS servers. Reverse DNS is disabled. Try using --system-dns or specify valid servers with --dns-servers
Nmap scan report for 192.168.0.25
Host is up (0.00013s latency).
PORT     STATE  SERVICE
9000/tcp closed cslistener
9000/udp closed cslistener

Nmap done: 1 IP address (1 host up) scanned in 0.09 seconds

```Found a forum post that referenced a Firestarter Firewall port policy event that suggested it resolved a similar port problem without difficulty and rather it appears that the problems with the ports are perhaps pertaining the "Network Connections" configuration, as that was done personally to work around the DHCP policy. Though the DSL section for the Network Connections were not configured & nor the IPv4 Route Tables and por verity have little experience with such. Was curious if anybody has any suggestions. 

Posteri decided to work with ufw & restarted the ufw & got ports 9000 open, though when doing a WAN nmap there are the results:

```
Starting Nmap 5.21 ( http://nmap.org ) at 2011-05-28 10:05 EET
Nmap scan report for adsl-76-242-191-0.dsl.okcyok.sbcglobal.net (76.242.191.0)
Host is up (0.0023s latency).
PORT     STATE  SERVICE
9000/tcp closed cslistener
9001/tcp closed tor-orport
9000/udp closed cslistener
9001/udp closed unknown

Nmap done: 1 IP address (1 host up) scanned in 0.15 seconds

```
Had a little chat with the developers within #opensim and it is rather the personal suggestion to permit technical aspects to the adults.

Gracias.

---

