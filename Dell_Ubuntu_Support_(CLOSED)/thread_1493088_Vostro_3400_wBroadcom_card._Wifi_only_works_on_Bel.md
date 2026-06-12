---
title: "Vostro 3400 w/Broadcom card. Wifi only works on Belkin Router?!?"
date: 2010-05-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bobv4 on 2010-05-25
[COLOR=black][FONT=Verdana]Hey guys.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I installed 10.04 a couple weeks ago and after successfully setting up my wireless card (Broadcom 4353 rev 01) using the Broadcom STA Driver, I am able to connect to my home router but nothing else! The router is a Belkin N wireless router running WPA2-Personal AES security. The wifi connects instantly and never drops connection.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I cannot connect to my other router a D-link DIR-628 running open, WEP, WPA, or WPA2 in any and all combinations (I tried everything I could think of for several hours). That router log says "MAC Address xxxxxxx disconnected due to deauthorization" which is crazy since this even happens when the router is running without any security. I know this particular router is crap so I'll assume the router is the problem there.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Worst of all I can't connect to my universities two wireless networks. One is WPA Enterprise, using a certificate (which is likely the issue) and the other an OPEN connection that requires a webpage login once you open your browser.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Right now I'm at school and iwconfig says:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]lo no wireless extensions.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]eth0 no wireless extensions.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]eth1 IEEE 802.11abgn ESSID:"" [/FONT][/COLOR]
[FONT=Verdana][COLOR=black]Mode:Managed Frequency:5.54 GHz Access Point: Not-Associated [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]Bit Rate:54 Mb/s Tx-Power:24 dBm [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]Retry min limit:7 RTS thr:off Fragment thr:off[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]Encryption key:off[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]Power Managementmode:All packets received[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]Link Quality=5/5 Signal level=0 dBm Noise level=-76 dBm[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]Rx invalid nwid:0 Rx invalid crypt:14 Rx invalid frag:0[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]Tx excessive retries:0 Invalid misc:0 Missed beacon:0[/COLOR][/FONT]
 
[COLOR=black][FONT=Verdana]So... is this really an issue with "Network manager" and should I get Wicd instead? Or, is this an issue with something else? (i.e. my university having insane security crap).[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Btw... this is a dual-boot system with Win 7 64-bit and the internet is flawless on that side.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks.[/FONT][/COLOR]

---

### Post by bobv4 on 2010-05-25
Internet connection to the WPA-Enterprise server is fixed! 
I just copied down all the windows 7 settings and found out the authentication method was wrong... needed PEAP and not TLS.

Still can't get the open network up... but at least I know it's not the Broadcom card!

---

