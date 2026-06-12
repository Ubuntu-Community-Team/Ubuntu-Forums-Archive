---
title: "Silly Question, but needs answering"
date: 2009-03-24
forum: General Help
---

### Post by iareConfusE on 2009-03-24
I've installed Ubuntu on an Acer Aspire one.  I've followed the steps to get the wireless working, but I'm not sure if it works, since I can't seem to find a place where I can choose a wireless network.  How do I see the list of available wireless networks?  I've poked around everywhere, tried to add more widgets to the panel, and came up with nothing.  

I've got the wireless LED's to start blinking upon wireless traffic, and I've checked the connection properties, and it seems to be sending and receiving packets.... but from what.. I don't know... It never asked me which wireless network I wanted to connect to, never asked me for a password or anything... I need to get this little icon in my taskbar somehow.

Any help would be appreciated, thanks.

---

### Post by 3Miro on 2009-03-24
In the top left corner (by default) you should see something like a network icon. It changes depending on what kind of network it is searching for/connecting to. When you click on it you should see all available networks.

From System -> Pref or Admin -> Network manager, there should be an option to enable/disable wireless. Might want to check that one too.

If you type ifconfig in the terminal, what do you get?

---

### Post by sailthesea on 2009-03-24
You may even already be connected! I can easily access unsecured networks just by booting up Try opening a browser if you didn't already, but you will need to identify your own network The tips above will get you going

---

### Post by iareConfusE on 2009-03-24
> **3Miro said:**
> In the top left corner (by default) you should see something like a network icon. It changes depending on what kind of network it is searching for/connecting to. When you click on it you should see all available networks.

From System -> Pref or Admin -> Network manager, there should be an option to enable/disable wireless. Might want to check that one too.

If you type ifconfig in the terminal, what do you get?

Here's what I get when I type ifconfig in terminal:
Right now I'm connected via cable (obviously), so I don't know if that would have any effect on the outcome of ifconfig.


ath0      Link encap:Ethernet  HWaddr 00:24:2b:15:6e:50  
          inet6 addr: fe80::224:2bff:fe15:6e50/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:23:8b:4e:7f:c8  
          inet addr:10.53.136.18  Bcast:10.53.136.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe4e:7fc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:490 errors:0 dropped:3064965536 overruns:0 frame:0
          TX packets:449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:501018 (501.0 KB)  TX bytes:80830 (80.8 KB)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-24-2B-15-6E-50-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:24
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:14753 (14.7 KB)  TX bytes:2300 (2.3 KB)
          Interrupt:18

---

### Post by iareConfusE on 2009-03-24
Oh snap, I fixed it.  Thanks for telling me where to find the option to enable it though, thats where I was able to type in my wireless network and log in.  My only question now is, how do I make it so that I don't have to type in the SSID for the specific router that I want to connect to?  I'm going to be using this netbook at school, and would like for the wireless card to be able to scan for various routers in range.

Thanks again guys.

---

### Post by lindsay7 on 2009-03-25
On the top menu bar go to System/Preferences/network connections.

You can set up you connections here, click on connect automatically.  When you roam, just pick the wireless source that you want to connect to.

---

### Post by 3rdalbum on 2009-03-25
Try typing this into the terminal (or adding it/enabling it in System > Preferences > Sessions > Startup Programs):

```
nm-applet
```

This will add a little applet to your panel that lists wireless networks, and can automatically connect to recently-used networks.

---

### Post by iareConfusE on 2009-03-25
> **lindsay7 said:**
> On the top menu bar go to System/Preferences/network connections.

You can set up you connections here, click on connect automatically.  When you roam, just pick the wireless source that you want to connect to.

Do I have to enable roaming or something?  I don't see an option or a tick box for "allow roaming" or anything of the like when I go System > Preferences > Network Configuration.

---

### Post by lindsay7 on 2009-03-25
No, you do not need to do anything.  Lets say you are downtown, you are going to pick up a number of wireless sites. Your adaptor will pick one, but you may want to pick one you think is safer or better, just  choose it. If it is someplace that you go to all the time, go to "network connections" and set up on you list. If it is a secure site you will need to add the key or passphrase.

---

### Post by iareConfusE on 2009-03-25
> **lindsay7 said:**
> No, you do not need to do anything.  Lets say you are downtown, you are going to pick up a number of wireless sites. Your adaptor will pick one, but you may want to pick one you think is safer or better, just  choose it. If it is someplace that you go to all the time, go to "network connections" and set up on you list. If it is a secure site you will need to add the key or passphrase.

Oh alright, thanks for clearing that up for me.

---

