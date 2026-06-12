---
title: "can't connect in Kubuntu or Ubuntu"
date: 2006-07-13
forum: Desktop Environments
---

### Post by maddbaron on 2006-07-13
My internet company verizon messed up my account so I wasnt able to connect to my network for the past week. I was using another network in my home. So now Verizon decides to fix my connection and I can connect via desktop (xp) and wirelessly via xp but when I boot into Kubuntu or Ubuntu my network gets picked up even has signal strength but no browsers or messengers work. firestarter works and picks up the network tho. Now when I set up my ubuntu months back i had to manually enter my dns info. I did that again just now b/c my dns changed but i still can't connect. is there a way to fix this in kubuntu? i want to connect wirelessly. I have my ppp ip and my main dns and sub dns info ready.

can someone help me and tell me what to input and where to do it?

---

### Post by philippe_carlo on 2006-07-13
Supposing your wireless interface is eth1:

Open up a console and do
```

sudo iwconfig eth1 essid <your network name>
sudo ifup eth1

```

If that does not work, post the output of these operations here.

---

### Post by maddbaron on 2006-07-13
after i entered 
> sudo ifup eth1
 i was told that 
> ifup: interface eth1 already configured

and my orange internet light started blinking none stop

---

### Post by philippe_carlo on 2006-07-13
Can you post the output of iwconfig and ifconfig here? 
Also run ping -c3 google.com

---

### Post by maddbaron on 2006-07-13
sorry took so long i tried to copy and paste konsole and send it via cable connection and even that doesnt work. had to save the konsole output in my windows drive and log into windows.
but here it is.
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"05B408580701"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:0E:10:19:B0
          Bit Rate:18 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-75 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

maddbaron@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:A3:21:48
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Base address:0x1800

eth1      Link encap:Ethernet  HWaddr 00:0E:9B:CD:84:0B
          inet addr:192.168.1.41  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:9bff:fecd:840b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2263 (2.2 KiB)  TX bytes:16010 (15.6 KiB)
          Interrupt:217 Memory:e2000000-e2002000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:256 (256.0 b)  TX bytes:256 (256.0 b)

maddbaron@ubuntu:~$ ping -c3.google.com
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination

---

### Post by maddbaron on 2006-07-13
now my system is going nuts!
 I logged out of xp and tried to restart linux and it wont load!
I am now getting kernal panic after a lot of text then i closed and restarted in recovery mode got a lot of text then stuff about ndiswrapper and wlan0 and my wireless card came up and now finally it is saying root@ubuntu:with the flickering light. 

i enter my password it said command not found same with my user name so now i am stuck on this screen.....

HELP PLEASE!

---

### Post by maddbaron on 2006-07-13
update:
I restarted again and it started normally thank god..will this kernal panic thing happen again? how can i avoid it?

also i activated the other network in my home and it connected to it. 

but my network doesnt work. 

so frustrating...i really hate verizon now.

---

### Post by maddbaron on 2006-07-13
still getting used to new visual style of this board. i see this belongs in the wireless help thread. once i figure out how to close this thread i will but until then i have reasked in the wireless help area. if anyone knows how to help me please reply there please.

---

### Post by randell6564 on 2006-07-13
just a thought...

Before you do all kinds of stuff at the console, try just unplugging your wireless and then wait a few seconds, plug it in and then check.

I use wireless on my box (XP and dapper) and it never fails... Every single time that I use XP and then log onto ubuntu, I have to reset my wireless by just unplugging it.

And another thing, cant you just use DHCP?

---

### Post by maddbaron on 2006-07-14
i generally dont use xp unless for dire emergency. and rarely to connect to the net anymore. just for file converting. always in kubuntu or ubuntu just stupid verizon took me off for a week and gave me a new ip now my system wont work wirelessly or dsl cable connectly. picks up network,name,strength but thats it. 

how do i configure DHCP in kubuntu or ubuntu?

---

### Post by randell6564 on 2006-07-14
> **maddbaron said:**
> i generally dont use xp unless for dire emergency. and rarely to connect to the net anymore. just for file converting. always in kubuntu or ubuntu just stupid verizon took me off for a week and gave me a new ip now my system wont work wirelessly or dsl cable connectly. picks up network,name,strength but thats it. 

how do i configure DHCP in kubuntu or ubuntu?

well... in Ubuntu, you go to System>Administration>Networking and click on your wireless connection, then click 'Properties' and you will see 'Connection Settings'.  Choose DHCP.

---

### Post by GuitarHero on 2006-07-14
i have this problem too but i never found a fix.

---

### Post by randell6564 on 2006-07-14
> **GuitarHero said:**
> i have this problem too but i never found a fix.

Did you manually correct your ip address?

---

### Post by GuitarHero on 2006-07-14
i just use dhcp

---

### Post by randell6564 on 2006-07-14
> **GuitarHero said:**
> i just use dhcp

EXACTLY!

For some reason, maddbaron cant see an option for DHCP.

---

### Post by GuitarHero on 2006-07-14
well i use dhcp but it still doesnt work.  the connection is shown with iwconfig but it wont fully connect or something so i cant actually use the internet.  its driving me mad

---

### Post by randell6564 on 2006-07-14
What are you on right now?

---

### Post by GuitarHero on 2006-07-14
windows laptop

---

### Post by randell6564 on 2006-07-14
> **GuitarHero said:**
> windows laptop

CHEATER! lol!

Are you useing a WEP key or anything other than just DHCP?

---

### Post by GuitarHero on 2006-07-14
its the only way i can troubleshoot.  i wanna get back to ubuntu.  its useless without internet though.

---

### Post by randell6564 on 2006-07-14
Are you useing a WEP key or anything other than just DHCP?

---

### Post by GuitarHero on 2006-07-14
nope, no wep.  Just essid and dhcp entered.  Should work, but it doesn't.

---

### Post by randell6564 on 2006-07-14
Crazy!

---

### Post by randell6564 on 2006-07-14
What hardware do you use?

---

