---
title: "Dell inspiron 1501, ethernet issue"
date: 2009-05-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by saisai on 2009-05-28
Hi I have a dell inspiron 1501, it came with windows XP but I completely reformatted it with Ubuntu 8.10 OS. But after I put in the ethernet cable, I dont get internet. Is it suppose to be plug and play? Or am I suppose to install a network driver? But I read in a forum that ethernet cable should work out of the box with 8.10.

Another thing that's confusing is when i first installed the OS, for a brief few seconds the network manager was able to automatically connect to "auto eth0" for like 2 seconds, and then it never connected again. I did manage to go to a webpage in those seconds, so I dont see why it would be a driver problem. the cable works fine. How would i go about fixing this?
thanks

here is the output of ifconfig -a:

[SIZE="1"][INDENT]sai@sai:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:15:c5:d0:55:bb
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:21

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:286 errors:0 dropped:0 overruns:0 frame:0
TX packets:286 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:18592 (18.5 KB) TX bytes:18592 (18.5 KB)

pan0 Link encap:Ethernet HWaddr 66:4c:e2:9b:96:8a
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wlan0 Link encap:Ethernet HWaddr 00:1a:92:23:b5:51
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wmaster0 Link encap:UNSPEC HWaddr 00-1A-92-23-B5-51-00-00-00-00-00-00-00-00-00-00
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
[/INDENT][/SIZE]

---

### Post by tricolorpoa on 2009-05-28
Well..

Is there aDHCP server in your network?
You can do a test editing your /etc/network/interface file to seems like these
```
auto lo
iface lo inet loopback

auto eth0
allow-hotplug eth0
iface eth0 inet dhcp

```

so run the command
```
$ sudo /etc/init.d/networking restart
```

If *ifconfig* do not show any IP Address you probaly do not have a DHCP serving IP address to your hosts...

---

### Post by spiceminesofkessel on 2009-05-28
You're right. Your wired Ethernet should work out of the box. Try checking a couple of things.

It's a stretch, but go to System -> Administration -> Hardware Drivers and make sure there are no proprietary drivers for your network card. I doubt you'll find any, but it's worth checking.

Go to System -> Preferences -> Network Connections and see if your network card is available or Auto eth0 is in the list. If so, click it and then click the Edit button. Authenticate. On the Wired tab, verify that the proper MAC address is listed and that the MTU is set to Automatic. Then, switch to the IPv4 Settings tab and verify that the Method is set to Automatic (DHCP). Click Apply if you made any changes.

If all of these options are properly set and you still cannot connect, you might have to try and manually assign your network card an IP address and see if that works.

---

### Post by saisai on 2009-05-28
Spiceminesofkessel:

In the hardware drivers it states "Proprietary drivers are being used to make this computer work properly".

I have two drivers both are proprietary according to the license. 
The first one is "wl" and it is activated. I dont know what "wl" means.
the second driver is ATI/AMD proprietary FGLRX graphics card. This one is deactivated.

So if it is proprietary what does that mean and what should I do?
how do I know what the proper MAC address should be?
thanks

---

### Post by saisai on 2009-05-28
tricolorpoa:

I added the lines:
auto eth0
allow-hotplug eth0
iface eth0 inet dhcp
to the /etc/network/interfaces 

and then ran the command sudo /etc/init.d/networking restart
it didnt work. I am really confused because I used to have ubuntu working but then last week the internet just stopped both on my ubuntu and XP partitions, so I decided to reformat my laptop entirely just with ubuntu.. But now I cant remember if the ethernet was plug and play or if I did it differently then..

---

### Post by spiceminesofkessel on 2009-05-28
I'm not 100% sure, but I think "wl" might stand for "wireless". It could be your wireless network card driver.

Proprietary means that the drivers are not open source (someone correct me if I'm wrong on that). You really don't have to do anything about that.

Now, I will assume the network card you are having issue with is eth0. When you typed, ifconfig -a, you got a lot of output. The MAC address for that card is in that output for eth0 under the lable of "HWaddr". According to your posted output, that would be:
> 00:15:c5:d0:55:bb

---

### Post by saisai on 2009-05-28
Ok then I guess my auto eth0 is properly configured.. 
I am thinking abt reinstalling the ubuntu OS again.

---

### Post by tricolorpoa on 2009-05-28
Probaly you have an network issue...
It is not seem to be a Ubuntu issue because XP doesn't work too..
What is your network address?
Maybe setting static IP can resolve your problem..

I am sure that your problem is with your DHCP server...

---

### Post by saisai on 2009-05-28
if theres another computer on the network could it confuse the DHCP server? (Not sure if that makes sense)
Right now I am using another laptop, Vista. Both the wireless and the cable works fine for this laptop..
When I run the OS off the CD I still cant get internet using the cable..
the hwaddr is 00:15:c5:d0:55:bb

---

### Post by tricolorpoa on 2009-05-28
The primary question:

Is there a DHCP server on your network?

---

### Post by saisai on 2009-05-28
How can I check if it is DHCP? I have a cable modem and a wireless router.

---

### Post by tricolorpoa on 2009-05-28
Você entende entende essa frase?

Check the Vista network configurations. If it is configured to obtain ip address automaticaly, and everything works fine, so you have a DHCP server on your network.!

;)

---

### Post by saisai on 2009-05-28
According to the vista, I have a DHCP server. What does that mean for my ubuntu? 

I am thinking about reinstalling XP, if internet still doesnt work with XP do you think its a hardware problem? or do you still think it's DHCP issue.

---

### Post by spiceminesofkessel on 2009-05-28
Just for kicks, type the following on your Ubuntu laptop:
```
ping 127.0.0.1
```
If this gives any kind of error, then you have a bad network card.

EDIT: Oh, use Ctrl+C (I believe) to stop the ping.

---

### Post by saisai on 2009-05-28
I pinged it to the localhost 127.0.0.1, no error received.
I don't think theres something wrong with the driver but I am wondering if I somehow disabled it? I know you can disable wireless on the keyboard but I am not sure if you can disable the card using keyboard?
**I installed ubuntu 9.04 and now under the "wired network" it says disconnected, instead of the autho eth0.**
A strange thing, just after I installed 9.04 for a few seconds it connected to auto eth0. it went on and off about 3 times.
And Now I have the wireless enabled and I can view the networks but the network manager is not recognizing my password... I have a broadcom STA wireless driver.

---

