---
title: "loosing wifi connection"
date: 2005-09-29
forum: Desktop Environments
---

### Post by lomomo on 2005-09-29
My wifi connection has been working fine since the first day i installed ubuntu, but a few weeks ago i started having problems, it now disconnects every few minuts.

My wifi card is detected as
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19

And i have no idea what is the problem and how to fix it, where can i look to see what is happening?? i don't see nothing in dmesg.

The network is working fine with other computer, so it's not a problem with the router or something else.

---

### Post by FLeiXiuS on 2005-09-29
Any recent software / configuration changes?  (EX: Updates / Tweaking..etc..)

---

### Post by lomomo on 2005-09-29
Only the ubuntu updates, security fixes i think.

---

### Post by FLeiXiuS on 2005-09-29
Hmm, give me some more information.   What's around the area your working under?  How far are you from the wireless AP?  Is there anything that'd block signal, concrete, walls, etc...? 

I'm sorry I just want to be sure it's not a physical problem.  Many people mis interpret that noise is an issue.

---

### Post by Wolki on 2005-09-29
Try the following:```
sudo iwconfig eth1 power off
sudo ifdown eth1
sudo ifup eth1
```

(replace eth1 with the correct interface)

If this doesn't work, save this as a text file:
```
#!/bin/bash
echo schalte wlan wieder an...
sudo /sbin/rmmod ipw2200 ieee80211 ieee80211_crypt_wep ieee80211_crypt
sudo /sbin/modprobe ipw2200
sudo /sbin/iwconfig eth1 power off
sudo ifdown eth1
sudo ifup eth1
echo fertig.
```
and make it executable, then run it. This fixed a problem i've been having on a relative's computer.

---

### Post by lomomo on 2005-09-30
[QUOTE=FLeiXiuS]Hmm, give me some more information.   What's around the area your working under?  How far are you from the wireless AP?  Is there anything that'd block signal, concrete, walls, etc...? 
I'm sorry I just want to be sure it's not a physical problem.  Many people mis interpret that noise is an issue.[/QUOTE]

I can touch the AP with my hand as i write this message, so there are not walls. The connection was working fine before and it works fine with my girlfriends computer (using ubuntu too). I don't think there's anything blocking the signal, and at the moment the network applet says i've 100% signal.

I tryed 
```

sudo iwconfig eth1 power off
sudo ifdown eth1
sudo ifup eth1

```

as suggested by wolky but it didn't work, i will try it's second suggestion next time it happens.

---

### Post by lomomo on 2005-09-30
the script proposed by wolki worked and i didn't have to reboot the system to restart the network connection, here's the output:

```

schalte wlan wieder an...
ERROR: Module ieee80211_crypt_wep does not exist in /proc/modules
ifdown: interface eth0 not configured
fertig.

```

But i still don't know why i'm loosing the connection. I don't want to run this script every few minuts.

---

### Post by Wolki on 2005-09-30
[QUOTE=lomomo]
But i still don't know why i'm loosing the connection. I don't want to run this script every few minuts.[/QUOTE]

I think it has to do with power saving and the card not waking up anymore. If the connection is active it should stay up.

---

### Post by lomomo on 2005-09-30
I don't think it's a power safe issue becaouse it happens when i'm working with the computer, browsing the web and having amule dowloading some files, so the internet connection is being used.

---

### Post by Wolki on 2005-09-30
[QUOTE=lomomo]I don't think it's a power safe issue becaouse it happens when i'm working with the computer, browsing the web and having amule dowloading some files, so the internet connection is being used.[/QUOTE]

Hm... that's waht it was on my relative's computer, I think

last time i edited the script (originally found on the german wiki, btw) to 

```
#!/bin/bash
/sbin/rmmod ipw2200 ieee80211 ieee80211_crypt_wep ieee80211_crypt
/sbin/modprobe ipw2200
/sbin/iwconfig eth1 power off
ifdown eth1
ifup eth1
```

And added a starter to the panel with "gksudo <script name>". Having it as an Icon is a little nicer than running the script manually. I hope this is fixed for breezy.

---

