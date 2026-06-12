---
title: "Internet just stopped working..."
date: 2009-04-06
forum: General Help
---

### Post by Ben Crisford on 2009-04-06
Solved now everyone.  Thank you *so* much for your replies.  You helped a great deal.

In the end it was vnet0 messing up my ath0.

Thanks again,
Ben

------------------------------------------

Yesterday my internet was working absolutely fine, and has been for ages.

But today it just isn't working.

I have been trying all morning, ive done countless reboots, re-installed my wireless card driver 5 times and I have tried disabling and re-enabling wireless and I have tried in KDE *and* gnome.

I'm almost certain I haven't changed *anything*.

Its an atheros wireless card, I don't know the exact model, if you need to know i'll do an lspci, just ask ;).

Anyway, please help, i'm desperate to get back on the internet.

**_Update:_**
I cannot ping anything apart from 127.0.0.1 (localhost) and I have tried a different adapter.

So it isn't the adapter.

Maybe there is a firewall or something...?  Help me :S...

---

### Post by Kareeser on 2009-04-06
Do you have a switch on the side of your computer to turn the wireless radio on and off?

... is it on? :)

---

### Post by 0per4t0r on 2009-04-06
You could try resetting your gateway, or establish a direct connection with an ethernet cable temporarily.

---

### Post by Ben Crisford on 2009-04-06
> **Kareeser said:**
> Do you have a switch on the side of your computer to turn the wireless radio on and off?

... is it on? :)

It was on yes :), and I just tried turning it off and on and it still didn't work.

> **0per4t0r said:**
> You could try resetting your gateway, or establish a direct connection with an ethernet cable temporarily.

There is no ethernet sockets anyware near my computer.  I'm on my old laptop temporarily, but it runs XP and i'm dying of frustration with it.


I think my problem might be with my DNS, but i'm not sure what.

Because it *says* im connected...

---

### Post by change_mode on 2009-04-06
Can you ping the router?

Can you ping google.com?

Can you ping 74.125.45.100 (google)?

---

### Post by Ben Crisford on 2009-04-06
> **change_mode said:**
> Can you ping the router?

Can you ping google.com?

Can you ping 74.125.45.100 (google)?

I can ping 74.125.45.100, I can't ping the router name or google.com but the router IP works.

---

### Post by Ben Crisford on 2009-04-06
Bump.

---

### Post by change_mode on 2009-04-06
> **Ben Crisford said:**
> I can ping 74.125.45.100, I can't ping the router name or google.com but the router IP works.

Try another DNS server.

---

### Post by Ben Crisford on 2009-04-06
> **change_mode said:**
> Try another DNS server.

Erm :S, how? :p lol

And I don't think it is my DNS, because when I used to use skype like *all* the time in windows, even when my DNS didn't, skype did.

However I suppose it could be different in skype for linux, so how would I go about trying another DNS server?

---

### Post by lykwydchykyn on 2009-04-06
If you can ping by ip but not by name, it's almost certainly DNS.  Try using opendns.
Instructions:
[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by change_mode on 2009-04-06
The ping results suggest that it's a fault with the DNS.
Skype possibly connects directly to the IP and doesn't need a DNS server.

There are two ways to change the DNS server. In the Ubuntu network config or in your router config.

---

### Post by Ben Crisford on 2009-04-06
> **lykwydchykyn said:**
> If you can ping by ip but not by name, it's almost certainly DNS.  Try using opendns.
Instructions:
[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

I followed the instructions...

It didn't work.  I still got a page not found.

---

### Post by Ben Crisford on 2009-04-06
> **change_mode said:**
> The ping results suggest that it's a fault with the DNS.
Skype possibly connects directly to the IP and doesn't need a DNS server.

There are two ways to change the DNS server. In the Ubuntu network config or in your router config.

I changed to openDNS and it didn't work :(.

***_Update:_***
I have been *very* stupid...  I couldn't actually ping the IPs...  It told me: "Operation not permitted" but I thought that was good :p.  All I can ping is localhost (127.0.0.1).

---

### Post by Ben Crisford on 2009-04-06
Another Update:

I have spent ages fiddling around with ndiswrapper to install another adapter and it is now connected through that but it still doesn't work.

Is there a firewall in Ubuntu or proxy that could be causing this?

---

### Post by Ben Crisford on 2009-04-06
bump.

---

### Post by Ben Crisford on 2009-04-06
Cmon guys, i'm desperate to get back on IRC.

I have 1001 things to do which I just, well can't...

---

### Post by Ben Crisford on 2009-04-06
Please...  Anyone...

I have important stuff to deal with on IRC...

Please...

---

### Post by lykwydchykyn on 2009-04-06
Why don't you give us that lspci info you mentioned earlier.  "dmesg |grep -i ath" might have some enlightening information as well.

---

### Post by Ben Crisford on 2009-04-06
lspci output for the adapter:
```
0c:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

I did the:
```
dmesg |grep -i ath
```
thing too...  But there is like loads of stuff :P.  Which bits should I post..?

---

### Post by change_mode on 2009-04-06
- your description of the problem is vague
- you don't seem to be completely computer illiterate, yet refuse to do anything on your own
- you don't read the replies
- you bump the topic all the time

Do you need any more reasons why people don't help you? I was going to, but there are the reasons I stopped bothering.

---

### Post by Ben Crisford on 2009-04-06
> **change_mode said:**
> - your description of the problem is vague
- you don't seem to be completely computer illiterate, yet refuse to do anything on your own
- you don't read the replies
- you bump the topic all the time

Do you need any more reasons why people don't help you? I was going to, but there are the reasons I stopped bothering.

Look alright, i'm sorry if I have annoyed you.  But I have read and replied to *every* single reply (and I have appreciated your help very much by the way).

You are saying I haven't done anything on my own, I posted this around midday having spent the whole morning trying to fix it.  I rebooted countless times, re-installed different drivers, and everything I have been advised to do.

I bump the topic all the time because I am so desperate to get back on the internet.  I have so much stuff to do, surely you understand.

Anyway I am sorry if I have frustrated you, and please don't stop helping as you have been a great help so far :).

**_Update:_**
I have just booted windows and internet works on it.  So its definately an ubuntu problem.

---

### Post by lykwydchykyn on 2009-04-06
> **Ben Crisford said:**
> 
```
dmesg |grep -i ath
```
thing too...  But there is like loads of stuff :P.  Which bits should I post..?

Post the important bits :-P

I don't know; does anything stand out as an error?  Can you pipe the output to a file and transfer it with a floppy or usb drive? e.g.:
```

dmesg|grep -i ath >errors.txt

```

---

### Post by change_mode on 2009-04-06
It would be nice to have some basic information without having to ask for it...
The PC you're posting from, same network?
Can you ping the Ubuntu PC from there?
Are you connected to a router? If so, does it show an active wireless connection or any other connection information?

You could try to boot with the Ubuntu live CD and see if internet works.
You could also install a packet sniffer like Wireshark to see what happens when you try to connect.

> **Ben Crisford said:**
> 
I have just booted windows and internet works on it.  So its definately an ubuntu problem.

Now that's some useful information ;) For now I'd install Wireshark and see what happens when you log the traffic. 

The network card should try to send out packets to connect to the network and we'll see what happens then.
You can also try to ping or something like that to check if any packets are being sent/received at all.

---

### Post by Ben Crisford on 2009-04-06
> **change_mode said:**
> It would be nice to have some basic information without having to ask for it...
The PC you're posting from, same network?
Can you ping the Ubuntu PC from there?
Are you connected to a router? If so, does it show an active wireless connection or any other connection information?

You could try to boot with the Ubuntu live CD and see if internet works.
You could also install a packet sniffer like Wireshark to see what happens when you try to connect.

Now that's some useful information ;) For now I'd install Wireshark and see what happens when you log the traffic. 

The network card should try to send out packets to connect to the network and we'll see what happens then.
You can also try to ping or something like that to check if any packets are being sent/received at all.

I'm posting from my old laptop which is on the same network yes.

It says I am connected to the internet (this is back with the broken one now) but it isn't.  I cannot ping my router.

I haven't actually tried with the live CD but I did start a virtual machine and tried in that (with the live CD ISO).

EDIT; I did the "dmesg|grep -i ath >errors.txt" and I did a control+f for "e" and couldn't see any errors, if I didn't look thouroughly tell me and i'll have a look, but it was all mac addresses and stuff so I didn't think there ws anything "error"y...

---

### Post by change_mode on 2009-04-06
Ok, live CD doesn't matter now. Just wanted to verify that the network card isn't broken. Now that we know the problem is Ubuntu specific, you should find out if the card is actually doing something or if it's dead. You can do that by logging the traffic as described in the previous posting.

If the network card doesn't work at all, maybe an update broke the drivers.

---

### Post by Ben Crisford on 2009-04-06
> **change_mode said:**
> Ok, live CD doesn't matter now. Just wanted to verify that the network card isn't broken. Now that we know the problem is Ubuntu specific, you should find out if the card is actually doing something or if it's dead. You can do that by logging the traffic as described in the previous posting.

If the network card doesn't work at all, maybe an update broke the drivers.

I'm pretty sure it isn't my adapter because I used a different one earlier and the internet still didn't work.

Is the a firewall that could be blocking me from going "outside the box" so to speak?

Thanks.

EDIT; Or is the network card not the adapter?  I'm a little confused, sorry.

---

### Post by change_mode on 2009-04-06
The firewall is disabled by default, because it's not needed. 
What exactly do you mean by adapter?

I'll check back here tomorrow.

---

### Post by Ben Crisford on 2009-04-07
> **change_mode said:**
> The firewall is disabled by default, because it's not needed. 
What exactly do you mean by adapter?

I'll check back here tomorrow.

Like the network adapter for conecting, its in-built but there still is an adapter right?  I tried with a different one earlier and still had the same problems.

Where are the firewall settings?  Do you know?  Because that sounds like the most likely cause to me.

Thanks,
Ben

---

### Post by Ben Crisford on 2009-04-07
I just went in KSystemLog and I searched for firewall (see first image attatched).

Does this mean something?

Also, when I open firefox and it doesn't let me connect if I have systemlog open it shows me that...  (see second image).

EDIT; Second image is harder to read here is what it says:
```
Apr 7 11:56:05 ben-laptop kernel: [ 5561.316166] IN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0b:6b:6c:45:d0:08:00:45:00:00...  SRC=192.168.2.4 DST=192.168.2.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=35127 PROTO=UDP SPT=137 DPT=137 LEN=58
Apr 7 11:56:05 ben-laptop kernel: [ 5561.316166] IN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0b:6b:6c:45:d0:08:00:45:00:00...  SRC=192.168.2.4 DST=192.168.2.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=35127 PROTO=UDP SPT=137 DPT=137 LEN=58
Apr 7 11:56:06 ben-laptop kernel: [ 5562.374823] IN= OUT=ath0 SRC=192.168.2.5 DST=208.67.222.222 LEN=69 TOS=0x00 PREC=0x00 TTL=64 ID=4873 DF PROTO=UDP SPT=44873 DPT=53 LEN=49
Apr 7 11:56:06 ben-laptop kernel: [ 5562.374823] IN= OUT=ath0 SRC=192.168.2.5 DST=208.67.222.222 LEN=69 TOS=0x00 PREC=0x00 TTL=64 ID=4873 DF PROTO=UDP SPT=44873 DPT=53 LEN=49

```
Basically, the first two lines get repeated 9 times (18 lines in total, but there is occasionally a line with different content, see below).

The second two lines get repeated 8 times (16 in total, but they are all the same as far as I can see).

From the section of the syslog I got this information from, there was one irregularity.  This line was among the 18 "IN=ath0 OUT=" lines but it was different.  Instead of being: (which the line above was)
```
Apr 7 11:55:52 ben-laptop kernel: [ 5561.316166] IN=ath0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0b:6b:6c:45:d0:08:00:45:00:00...  SRC=192.168.2.4 DST=192.168.2.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=35127 PROTO=UDP SPT=137 DPT=137 LEN=58

```

It was:

```
Apr 7 11:56:05 ben-laptop kernel: [ 5561.316166] IN=ath0 OUT= MAC=01:00:5e:00:00:fb:00:0b:6b:45....  SRC=192.168.2.4 DST=225.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=35367 PROTO=2

```
There were several of these irregular results popping up in certain places around the log.

NOTE; I did not fill out the whole "MAC=" because they are so long and I cannot copy and paste, it took me about half an hour to fill out all that code, so I didn't get time for the full MAC.

---

### Post by change_mode on 2009-04-07
To see the firewall rules, you can use

```
sudo iptables -L
```

I don't think that's the problem though, as these entries don't just change for no reason and I think they also reset to default after every session.


> **Ben Crisford said:**
> Like the network adapter for conecting, its in-built but there still is an adapter right?  I tried with a different one earlier and still had the same problems.

So you got two network cards? If you're only using one, you should disable the other one in the BIOS (onboard LAN = disable).

> **Ben Crisford said:**
> 
NOTE; I did not fill out the whole "MAC=" because they are so long and I cannot copy and paste, it took me about half an hour to fill out all that code, so I didn't get time for the full MAC.

Copy/paste should work in the system log ;) There are two different source IPs in the packet logs, 192.168.2.4 and 192.168.2.5 - what's the matter with that?

Looks like a messed up network config. Could you post the output of

```
route -n
```

---

### Post by Ben Crisford on 2009-04-07
```
ben@ben-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 ath0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 vnet0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 ath0


```

There is the output.

And no I don't have two on board wireless cards, I have one which I am using now on my old PC and my new pc (the broken one) has one in-built.  What I mean is that my new PC's internet still doesn't work with the other card.

Ben

---

### Post by change_mode on 2009-04-07
Can you post the output of

```
ifconfig
```

Do you use DHCP or static IPs?

---

### Post by frodon on 2009-04-07
BTW, what version of ubuntu are you running ?

---

### Post by Ben Crisford on 2009-04-07
> **change_mode said:**
> Can you post the output of

```
ifconfig
```

Do you use DHCP or static IPs?

I don't know what IPs tbh :S, sorry.

Here is the output:
```
ben@ben-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:15:af:9f:0f:48  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe9f:f48/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1314 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:103326 (103.3 KB)  TX bytes:1152 (1.1 KB)

eth0      Link encap:Ethernet  HWaddr 00:1b:38:d6:a5:97  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2076 (2.0 KB)  TX bytes:2076 (2.0 KB)

vnet0     Link encap:Ethernet  HWaddr 42:09:60:34:f7:2c  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::4009:60ff:fe34:f72c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-15-AF-9F-0F-48-37-32-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:124609 errors:0 dropped:0 overruns:0 frame:43
          TX packets:5709 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:10888395 (10.8 MB)  TX bytes:296926 (296.9 KB)
          Interrupt:17 


```

> **frodon said:**
> BTW, what version of ubuntu are you running ?

8.10, my profile says jaunty, but now alpha is over i'm waiting for the final release.

---

### Post by change_mode on 2009-04-07
It says that your network card received more than 10mb of data so something works... now it would be interesting to know where the data goes (the packet logging I suggested earlier could possibly help with that).

Must be a configuration or drivers problem, but I'm not really an expert with wireless configuration, so maybe someone else can help you with that. They'd probably want to know what drivers you're using and how you installed them.

---

### Post by Ben Crisford on 2009-04-07
> **change_mode said:**
> It says that your network card received more than 10mb of data so something works... now it would be interesting to know where the data goes (the packet logging I suggested earlier could possibly help with that).

Must be a configuration or drivers problem, but I'm not really an expert with wireless configuration, so maybe someone else can help you with that. They'd probably want to know what drivers you're using and how you installed them.

Drivers for what?  I know its not my card thats the problem as internet still doesn't work with a different card.

What I noticed was that it seems to only be receiving data from my router, I might be wrong but I think I saw that (sorry, but I don't remember which command I was told me to do showed me that)...

So perhaps something doesn't want me to connect to the "outside world" so to speak...

Internet works fine in vista...

---

### Post by change_mode on 2009-04-07
> **Ben Crisford said:**
> Drivers for what?  I know its not my card thats the problem as internet still doesn't work with a different card.

What I noticed was that it seems to only be receiving data from my router, I might be wrong but I think I saw that (sorry, but I don't remember which command I was told me to do showed me that)..

The linux wireless drivers.

All the incoming internet data comes from the router so that's not a problem. If something was blocking your access, your windows access would most likely be blocked too and you wouldn't receive any data at all. 10 mb received data is quite a lot for a connection that's not working. 
It's certainly a linux wireless driver/configuration problem.

---

### Post by Ben Crisford on 2009-04-07
> **change_mode said:**
> The linux wireless drivers.

All the incoming internet data comes from the router so that's not a problem. If something was blocking your access, your windows access would most likely be blocked too and you wouldn't receive any data at all. 10 mb received data is quite a lot for a connection that's not working. 
It's certainly a linux wireless driver/configuration problem.

If madwifi is a linux wireless driver then I use that.

And I have re-installed it many times in the last few days...

What does this mean :S?

Thanks,
Ben

---

### Post by dtoronto on 2009-04-07
> I can ping 74.125.45.100, I can't ping the router name or google.com but the router IP works.

Sounds like its a problem with your router you may need to replace.

---

### Post by dtoronto on 2009-04-07
> Another Update:

I have spent ages fiddling around with ndiswrapper to install another adapter and it is now connected through that but it still doesn't work.

sorry didn't read this post.  It's a driver issue.  I don't know enough about wireless and Ubuntu to help out, but you may want to post which driver you are using and what kind of wireless card you are using.

---

### Post by Ben Crisford on 2009-04-07
> **dtoronto said:**
> sorry didn't read this post.  It's a driver issue.  I don't know enough about wireless and Ubuntu to help out, but you may want to post which driver you are using and what kind of wireless card you are using.

I think my card is posted on page 2.

Every other computer on my network is working fine, and it doesn't work even if I use a different card, so I didn't think it was a card issue.

---

### Post by change_mode on 2009-04-07
> **Ben Crisford said:**
> If madwifi is a linux wireless driver then I use that.

And I have re-installed it many times in the last few days...

What does this mean :S?

Thanks,
Ben

When you uninstalled the driver, did you use the purge option? Otherwise it might just keep the configuration files and nothing will change.

If that doesn't work, you might consider making a more descriptive topic like 'wireless problem' or something like that, to make sure the right people read it and can help (and include the important info from this topic). Anyway, good luck.

---

### Post by Ben Crisford on 2009-04-07
> **change_mode said:**
> When you uninstalled the driver, did you use the purge option? Otherwise it might just keep the configuration files and nothing will change.

If that doesn't work, you might consider making a more descriptive topic like 'wireless problem' or something like that, to make sure the right people read it and can help (and include the important info from this topic). Anyway, good luck.

How would I go about purging it?  I just simply re-installed it.

I just "cd"'d into the directory and did make, make install and modprobe ath_pci...

---

### Post by nothingspecial on 2009-04-07
You may have had a kernel update. When you installed the madwifi driver it attached itself to the kernel, now you have a new one you`ve got to do it again.

If you still have your original madwifi directory this is easy.

navigate into it from the terminal using the cd command then

```
make clean
```
```
sudo make install
```

I see you`ve tried reinstalling it so if that doesn`t work, I`m not sure

---

### Post by Ben Crisford on 2009-04-07
> **nothingspecial said:**
> You may have had a kernel update. When you installed the madwifi driver it attached itself to the kernel, now you have a new one you`ve got to do it again.

If you still have your original madwifi directory this is easy.

navigate into it from the terminal using the cd command then

```
make clean
```
```
sudo make install
```

I see you`ve tried reinstalling it so if that doesn`t work, I`m not sure

It didn't work :(.  It still says "Address Not Found" when I go into firefox :'(.

Cheers anyway though ;).

And I don't think it can be drivers, it always finds and connects to the network, but it won't let me do anything on the internet.

---

### Post by Ben Crisford on 2009-04-07
:( This is on page 4 now....

---

### Post by Ben Crisford on 2009-04-08
This is on page 9 now :(.

Someone help, please...

---

### Post by lykwydchykyn on 2009-04-08
> **Ben Crisford said:**
> 
I haven't actually tried with the live CD but I did start a virtual machine and tried in that (with the live CD ISO).


This isn't going to work; a virtual machine just tunnels through your host-machine connection, so if that isn't working the virtual machine obviously isn't going to work.

If you haven't yet, boot to a liveCD for real and see if your card works.  If it does, well we know where the problem lies.  At worst case scenario you can back up /home and reinstall.

Can we see the contents of /etc/resolv.conf as well?  What we know so far is:
 - You have an IP address.  This means you're connected to the router wirelessly and able to communicate with it.
 - You have a gateway.  This means you can send and receive data from outside the network.
 - We don't know if you can resolve network names -- that's why I need to see resolv.conf.
 - We have not seen what firewall rules are active -- you could see this with the command "sudo iptables -L"

---

### Post by Ben Crisford on 2009-04-08
> **lykwydchykyn said:**
> This isn't going to work; a virtual machine just tunnels through your host-machine connection, so if that isn't working the virtual machine obviously isn't going to work.

If you haven't yet, boot to a liveCD for real and see if your card works.  If it does, well we know where the problem lies.  At worst case scenario you can back up /home and reinstall.

Can we see the contents of /etc/resolv.conf as well?  What we know so far is:
 - You have an IP address.  This means you're connected to the router wirelessly and able to communicate with it.
 - You have a gateway.  This means you can send and receive data from outside the network.
 - We don't know if you can resolve network names -- that's why I need to see resolv.conf.
 - We have not seen what firewall rules are active -- you could see this with the command "sudo iptables -L"

I'll boot from live now, then i'll do the resolv.conf and iptables -L.

Cheers,
Ben

EDIT;  I booted from live.  It didn't find the network at all, this is because (i think) I would need my driver installed, it was fiddly to install.

And I cannot do that on live :S.

I'll do the other stuff now ;).

---

### Post by kryptikos on 2009-04-08
This is a DNS issue on the ubuntu side. The card is coming up just fine because he can ping by IP address. The route -n shows routing. He can ping his router. It's not a driver issue on the NIC card. 

He stated his network works fine on XP. What I am curious is what DNS is being handed out to  your XP box? From DOS command line (start -> run -> type "cmd") enter the command: **ipconfig /all** and let us know the IP listed in DNS Servers.

Once you have that we need to see what is listed in the /etc/resolv.conf file when your ubuntu boots up. These should be the same. Your home router should pick up an IP address and DNS information from your ISP. The router will then handle the DNS for your box. 

Let us know that contents of those settings.

---

### Post by Ben Crisford on 2009-04-08
> **kryptikos said:**
> This is a DNS issue on the ubuntu side. The card is coming up just fine because he can ping by IP address. The route -n shows routing. He can ping his router. It's not a driver issue on the NIC card. 

He stated his network works fine on XP. What I am curious is what DNS is being handed out to  your XP box? From DOS command line (start -> run -> type "cmd") enter the command: **ipconfig /all** and let us know the IP listed in DNS Servers.

Once you have that we need to see what is listed in the /etc/resolv.conf file when your ubuntu boots up. These should be the same. Your home router should pick up an IP address and DNS information from your ISP. The router will then handle the DNS for your box. 

Let us know that contents of those settings.

When I said I could ping IPs I was mistaken...  I read it wrong, I posted that I was wrong somewhere on the thread :S, but not sure where :S.

Sure i'll boot vista and do a ipconfig from cmd, but i'm not sure what it'll tell us...

I changed DNS by the suggestion of a poster on this thread and my internet still didnt work :/.

I'll do the ipconfig now for you.

I have both files, but my pen drive is playing up :S.

I'll post it here as soon as possible (hopefully soon).

---

