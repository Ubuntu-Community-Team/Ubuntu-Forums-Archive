---
title: "Banshee keeps pausing during Radio Stream."
date: 2009-06-23
forum: General Help
---

### Post by toejamfootball on 2009-06-23
I am on a 1.5MB down ADSL connection so it isn't stopping to buffer.

Any thoughts? Is there a better program I should be using to stream online radio?

Thanks guys.

---

### Post by blueridgedog on 2009-06-23
As an idea, try running "top" in a terminal to see if an application is using a lot of the CPU during the pause.  

Next, you may consider using tcpdump to watch the stream of packets, just to verify that the pause is on your end.

---

### Post by toejamfootball on 2009-06-24
> **blueridgedog said:**
> As an idea, try running "top" in a terminal to see if an application is using a lot of the CPU during the pause.  

Next, you may consider using tcpdump to watch the stream of packets, just to verify that the pause is on your end.
Thanks for your response. Banshee is using between 3-16% when streaming, but it doesn't spike or anything when it pauses. Nothing else does either.

I tried typing tcpdump in the terminal and got nothing, I guess I am doing this wrong? Thanks again.

The stream works fine using VLC.... Hmmm...

---

### Post by toejamfootball on 2009-06-25
Stream also works fine with Rhythmbox. So I'm pretty sure the problem is with Banshee.

---

### Post by toejamfootball on 2009-06-26
This is what is printed when Banshee pauses the Stream

```
15:01:43.713984 IP 202.6.74.107.8060 > james-desktop1.local.52004: . ack 186 win 6432 <nop,nop,timestamp 1037111428 4198912>
15:01:47.298967 IP james-desktop1.local.37937 > by2msg3020507.phx.gbl.msnp: P 35:40(5) ack 57 win 1002 <nop,nop,timestamp 4199814 23956039>
15:01:47.472022 IP by2msg3020507.phx.gbl.msnp > james-desktop1.local.37937: P 57:65(8) ack 40 win 65355 <nop,nop,timestamp 23956340 4199814>
15:01:47.472072 IP james-desktop1.local.37937 > by2msg3020507.phx.gbl.msnp: . ack 65 win 1002 <nop,nop,timestamp 4199857 23956340>
15:01:48.809455 IP james-desktop1.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? _daap._tcp.local. (34)
15:01:49.158122 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 252
15:01:49.158717 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 270
15:01:49.159325 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 324
15:01:49.160551 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 316
15:01:49.162114 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 246
15:01:49.162730 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 288
15:01:49.163971 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 320
15:01:49.165507 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 266
15:01:49.166104 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 318
15:01:49.167347 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 312
15:01:49.168874 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 244
15:01:49.169456 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 287
15:01:49.170689 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 317
15:02:00.927325 IP james-desktop1.local.40392 > a550.g.akamai.net.www: F 2161905740:2161905740(0) ack 103954457 win 588 <nop,nop,timestamp 4203221 213487866>
15:02:00.927595 IP james-desktop1.local.49059 > 192.168.0.1.domain: 31081+ PTR? 137.28.26.203.in-addr.arpa. (44)
15:02:00.958972 IP a550.g.akamai.net.www > james-desktop1.local.40392: F 1:1(0) ack 1 win 3752 <nop,nop,timestamp 213790384 4203221>
15:02:00.959028 IP james-desktop1.local.40392 > a550.g.akamai.net.www: . ack 2 win 588 <nop,nop,timestamp 4203229 213790384>
15:02:01.028093 IP 192.168.0.1.domain > james-desktop1.local.49059: 31081*- 1/0/0 (75)
15:02:09.160590 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 252
15:02:09.161182 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 270
15:02:09.161790 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 324
15:02:09.163016 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 316
15:02:09.164577 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 246
15:02:09.165174 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 288
15:02:09.166414 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 320
15:02:09.167960 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 266
15:02:09.168556 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 318
15:02:09.169799 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 312
15:02:09.171472 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 244
15:02:09.172076 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 287
15:02:09.173317 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 317
15:02:10.299223 IP james-desktop1.local.58325 > bos-m018a-sdr1.blue.aol.com.aol: P 42:48(6) ack 1 win 63920
15:02:10.541948 IP bos-m018a-sdr1.blue.aol.com.aol > james-desktop1.local.58325: . ack 48 win 16384
15:02:17.299092 IP james-desktop1.local.37937 > by2msg3020507.phx.gbl.msnp: P 40:45(5) ack 65 win 1002 <nop,nop,timestamp 4207314 23956340>
15:02:17.472415 IP by2msg3020507.phx.gbl.msnp > james-desktop1.local.37937: P 65:73(8) ack 45 win 65350 <nop,nop,timestamp 23956640 4207314>
15:02:17.472464 IP james-desktop1.local.37937 > by2msg3020507.phx.gbl.msnp: . ack 73 win 1002 <nop,nop,timestamp 4207357 23956640>
15:02:29.162901 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 252
15:02:29.163491 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 270
15:02:29.164099 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 324
15:02:29.165326 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 316
15:02:29.166875 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 246
15:02:29.167484 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 288
15:02:29.168740 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 320
15:02:29.170262 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 266
15:02:29.170860 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 318
15:02:29.172081 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 312
15:02:29.173586 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 244
15:02:29.174200 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 287
15:02:29.175427 IP 192.168.0.1.1900 > 239.255.255.250.1900: UDP, length 317

```

When I stream with VLC the "UDP" lines only come up every minute or so, whereas these thee groups came up as soon as Banshee paused the steam. Not sure what any of this means :D

---

### Post by blueridgedog on 2009-06-26
Excellent.  You have gotten TCP Dump to work.  It is a great tool.  Addresses over 223.255.255.255 are multicast addresses and the next step is to figure out why your system tries to multicast when Banshee is running.  

Have you installed any plugins?

Port 1900 is the announce port fo UPnP devices ([http://www.grc.com/port_1900.htm](http://www.grc.com/port_1900.htm)), so perhaps you can turn it off.  Try disabling the DAAP extension in the Banshee options.

---

### Post by toejamfootball on 2009-06-26
> **blueridgedog said:**
> Excellent.  You have gotten TCP Dump to work.  It is a great tool.  Addresses over 223.255.255.255 are multicast addresses and the next step is to figure out why your system tries to multicast when Banshee is running.  

Have you installed any plugins?

Port 1900 is the announce port fo UPnP devices ([http://www.grc.com/port_1900.htm](http://www.grc.com/port_1900.htm)), so perhaps you can turn it off.  Try disabling the DAAP extension in the Banshee options.
The only plugins are the ones that come with it, I think they are all active on a standard install....

I switched off DAAP. It still prints those groups between every 30 - 60seconds. It hasn't paused yet, but it is 4AM so maybe the fact that no-one is listening has something to do with that?

Thanks for your help so far man.

---

### Post by blueridgedog on 2009-06-26
The next thing I would try is turning the all off...(the plugins that is).  I think Banshee is clearly trying to multicast that it is running and can talk to UPnP devices.  I bet you see the packets even when you are not streaming, but when Banshee is merely running...

---

### Post by toejamfootball on 2009-06-27
Those packets show up even when Banshee isn't running. I have disabled all Plugins except Radio and it seems to be working so far....

Could it have something to do with my router? In the router settings there is "Multicast Streams" and it is Enabled???

We'll see how it goes....

Thanks man.

---

