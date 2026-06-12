---
title: "Crossover Cable Internet Connection Sharing with DSL Modem"
date: 2005-11-29
forum: Desktop Environments
---

### Post by shaggydoo on 2005-11-29
[Solved: [http://ubuntuforums.org/showthread.php?p=532091#post532091]("http://ubuntuforums.org/showthread.php?p=532091#post532091")]

Hi,

Well, I've been trying to get this to work for HOURS. I've googled and searched on this site all I can, but nothing seems to help (not being able to download dnsmasq doesn't seem to help, either).

Here's my situation:

Previously, I had two Windows XP machines, a laptop and a desktop. The desktop now runs on Ubuntu, the laptop is still XP (but occasionally OSx86). 

I had everything connected as follows:
```
DESKTOP NIC 1 --> MODEM
DESKTOP NIC 2 -crossover cable-> LAPTOP
```

Using my DSL modem's capabilities to dial-in on the modem itself, I no longer had to dial in with PPPOE on my XP desktop.

However, due to the way it was blocking incoming traffic, I couldn't have a webserver (I use it for testing and all that jazz) running on my laptop visible to people outside my network, so I gave LAPTOP a static IP, meaning it couldn't use ICS in the traditional sense, instead, it allowed me to pass-through NIC2 to MODEM, so I could dial-in manually on PPPOE on LAPTOP. This way LAPTOP has it's own seperate IP, while DESKTOP and MODEM share the same IP.


Now, with Ubuntu, I just can't seem to get this kind of relationship going! I can't even do a basic internet connection share (remember, my modem is always connected to the net).

Could anyone please help me with this? This is truely the only onion in the ointment that cures Windows. In short: I want to share an internet connection with two computers via crossover cable.

---

### Post by akiro.yamamoto on 2005-11-29
Please post any details you have from the Network Settings Dialog with regards any/all detected networks/connections to help us get you through this....
Of course what you're really trying to do is enable Internet Connection Sharing to allow the laptop access to the internet as well as use the Desktop with Ubuntu on it to act as the main firewall for your network right??
Regards

---

### Post by akiro.yamamoto on 2005-11-29
I googled for Ubuntu: Internet Connection Sharing and found this Post in Our
Forum:
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)
I hope this helps.
Regards
:smile:

---

### Post by shaggydoo on 2005-11-29
Thanks for the reply, akiro, but I tried that and it didn't work. For some reason, after I do that, not only am I still not able to ping the laptop (or vice-versa) or use the Internet on it, I can no longer access the Internet on the Ubuntu desktop. Disabling ipmasq gets me back on, but the problem is still there.

Strangely enough, I disabled eth0 and gave eth1 a static IP. Then, for some odd reason, the computers still wouldn't even directly connect. I had to enable eth0 and plug the laptop into there (rather than the modem being connected to eth0, I'm trying to FTP into the laptop), why would that happen? I'm thinking there's some sort of config problem with eth1.

Also, after I set up dnsmasq and ipmasq, I can't seem to have both eths enabled at the same time, or I lose connection to the Internet.

And if you need info from any commands about the computer(s), let me know and I'll post them.

---

### Post by cwaldbieser on 2005-11-29
[QUOTE=shaggydoo]Thanks for the reply, akiro, but I tried that and it didn't work. For some reason, after I do that, not only am I still not able to ping the laptop (or vice-versa) or use the Internet on it, I can no longer access the Internet on the Ubuntu desktop. Disabling ipmasq gets me back on, but the problem is still there.

Strangely enough, I disabled eth0 and gave eth1 a static IP. Then, for some odd reason, the computers still wouldn't even directly connect. I had to enable eth0 and plug the laptop into there (rather than the modem being connected to eth0, I'm trying to FTP into the laptop), why would that happen? I'm thinking there's some sort of config problem with eth1.

Also, after I set up dnsmasq and ipmasq, I can't seem to have both eths enabled at the same time, or I lose connection to the Internet.

And if you need info from any commands about the computer(s), let me know and I'll post them.[/QUOTE]

Could you post the output of these commands from each computer?
```

$ ifconfig
$ route

```

---

### Post by dcstar on 2005-11-29
[QUOTE=shaggydoo]
......
Could anyone please help me with this? This is truely the only onion in the ointment that cures Windows. In short: I want to share an internet connection with two computers via crossover cable.[/QUOTE]
Do yourself a big favour, purchase a small switch/router and just plug everything into it.

That way your laptop and PC will be able to independently access the 'net, and you won't have to stuff around with routing via the PC.

For the price of a few dollars you will end up with a much more reliable setup.

---

### Post by matthew on 2005-11-29
[quote=shaggydoo]I had everything connected as follows:
```
DESKTOP NIC 1 --> MODEM
DESKTOP NIC 2 -crossover cable-> LAPTOP
``` 
Using my DSL modem's capabilities to dial-in on the modem itself, I no longer had to dial in with PPPOE on my XP desktop.

Now, with Ubuntu, I just can't seem to get this kind of relationship going! I can't even do a basic internet connection share (remember, my modem is always connected to the net).

Could anyone please help me with this? [/quote]
This howto isn't exactly the same, but some of the setup info will apply to what you are trying to do. I suggest you take a look and see if you can adapt it to your needs.
[http://ubuntuforums.org/showthread.php?t=76346](http://ubuntuforums.org/showthread.php?t=76346)

---

### Post by shaggydoo on 2005-11-30
Nevermind, everyone! Thanks for all the help, guys, I managed to figure it out myself. I had to bridge my connections and add the default gateway for my bridge, now it works! **[SIZE="5"][COLOR="RED"]SOLVED![/color][/SIZE]**

I'm not all too good, so I basically had to figure it all out on my own. I found out about the bridge command (brctl) and I saw how to set up the gateway from another post (route), and ifconfig was pretty self-explanatory.

DSL modem is at 192.168.2.1
eth0 connects to my modem/Internet
eth1 connects to my laptop
br0 is the bridge I made between these two.

[LIST=1]
[*]# take the ethernet cards down
ifconfig eth0 down
ifconfig eth1 down
[*]# create a bridge, then add eth0 and eth1 to it
brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1
[*]# assign ips appropriately
ifconfig br0 192.168.2.10
ifconfig eth0 192.168.2.2
ifconfig eth1 192.168.2.3
[*]# put the bridge and ethernets back up
ifconfig br0 up
ifconfig eth0 up
ifconfig eth1 up
[*]# set up the gateway
route add default gw 192.168.2.1 br0
[/LIST]

Then, BAM! Connection was working on both computers. What a learning experience, I now know one thousand times more about networking than I ever did. **Windows and Ubuntu can get along!**



**[COLOR="Red"]Update:[/COLOR]** As it turns out, rebooting completely wipes my network settings, so I had to create a startup script to init all my settings during the bootup:
```
#!/bin/bash
# take down the ethernet cards
echo 'BN: Shutting down ethernet'
gksudo 'ifconfig eth0 down'
gksudo 'ifconfig eth1 down'
# create a bridge, then add eth0 and eth1 to it
echo 'BN: Creating bridge'
gksudo 'brctl addbr br0'
gksudo 'brctl addif br0 eth0'
gksudo 'brctl addif br0 eth1'
# assign ips appropriately
echo 'BN: Registering ethernet addresses'
gksudo 'ifconfig br0 192.168.2.10'
gksudo 'ifconfig eth0 192.168.2.2'
gksudo 'ifconfig eth1 192.168.2.3'
# put the bridge and ethernets back up
echo 'BN: Initializing bridged network'
gksudo 'ifconfig br0 up'
gksudo 'ifconfig eth0 up'
gksudo 'ifconfig eth1 up'
# set up the gateways
echo 'BN: Routing bridged network'
gksudo 'route add default gw 192.168.2.1 br0'
```

All looks well, I love Ubuntu already!

---

