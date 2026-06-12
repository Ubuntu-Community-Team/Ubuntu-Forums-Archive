---
title: "Steam won't update"
date: 2021-06-15
forum: Gaming &amp; Leisure
---

### Post by davoudi on 2021-06-15
So I manage to install steam on my desktop, Ubuntu 20.04, following this [page]("https://linuxconfig.org/how-to-install-steam-on-ubuntu-20-04-focal-fossa-linux"). Steam as usual start by checking for new update. Unfortunately steam stuck at update and exits by the following message: Fatal Error: Steam needs to be online to update. Please confirm your network connection and try again.

---

### Post by davoudi on 2021-06-15
After a long search I found this [solution]("https://askubuntu.com/questions/1318238/steam-install-not-finding-internet-connection-on-ubuntu-20-04"). I get nothing from pinging to this address: [FONT=monospace][COLOR=#000000]media.steampowered.com. [/COLOR][/FONT]This is the result of ping after I use ctrl +c :

> 
[FONT=monospace][COLOR=#000000]PING a1843.b.akamai.net (23.58.223.138) 56(84) bytes of data.[/COLOR]
^C
--- a1843.b.akamai.net ping statistics ---
646 packets transmitted, 0 received, 100% packet loss, time 660475ms
[/FONT]

---

### Post by mastablasta on 2021-06-16
there are a few install methods in your firts link. which one did you use? repository?

have you run the ubuntu updates? sometimes steam updates through them.

1. run ubuntu updates
2. try launching steam

if it still doesn't work, i would remove it and reinstall it. i believe you can remove it while keeping any installed games on disk. we have 3 steam installs at home and so far there was only one issue when steam created a gigantic log file. nothing after i resolved that.

---

### Post by davoudi on 2021-06-16
> **mastablasta said:**
> 
there are a few install methods in your firts link. which one did you use? repository?

 I used repository: sudo apt install steam.

> **mastablasta said:**
> 
have you run the ubuntu updates? sometimes steam updates through them.

 Yes, I update and upgrade.

> **mastablasta said:**
> 
1. run ubuntu updates
2. try launching steam

 No change. :(

> **mastablasta said:**
> 
if it still doesn't work, i would remove it and reinstall it. i believe you can remove it while keeping any installed games on disk. we have 3 steam installs at home and so far there was only one issue when steam created a gigantic log file. nothing after i resolved that.

 I remove it and install it again for several times but no change.

---

### Post by davoudi on 2021-06-16
I even use Lutris to install steam games but I encounter to same error. I believe that Lutris uses winesteam instead of steam. I think the problem is not due to installation.

---

### Post by davoudi on 2021-06-16
By the way why the output of ping shows the attempt to address [COLOR=#000000][FONT=monospace]*a1843.b.akamai.net instead of *[/FONT][/COLOR][COLOR=#000000][FONT=monospace]media.steampowered.com?[/FONT][/COLOR]

---

### Post by mastablasta on 2021-06-18
i also get akamai.net. but in my case it pings back.
```
[FONT=monospace][COLOR=#000000]ping media.steampowered.com [/COLOR]
PING a1843.b.akamai.net (193.77.14.152) 56(84) bytes of data. 
64 bytes from 193.77.14.152 (193.77.14.152): icmp_seq=1 ttl=61 time=2.05 ms 
64 bytes from 193.77.14.152 (193.77.14.152): icmp_seq=2 ttl=61 time=2.33 ms 
64 bytes from 193.77.14.152 (193.77.14.152): icmp_seq=3 ttl=61 time=2.26 ms 
64 bytes from 193.77.14.152 (193.77.14.152): icmp_seq=4 ttl=61 time=2.34 ms 
64 bytes from 193.77.14.152 (193.77.14.152): icmp_seq=5 ttl=61 time=2.37 ms 
64 bytes from 193.77.14.152 (193.77.14.152): icmp_seq=6 ttl=61 time=2.46 ms 
^C 
--- a1843.b.akamai.net ping statistics --- 
6 packets transmitted, 6 received, 0% packet loss, time 5009ms 
rtt min/avg/max/mdev = 2.055/2.306/2.462/0.129 ms

[/FONT]
```

I checked the IP and it is from my internet provider.

you get: > [FONT=monospace]646 packets transmitted, 0 received, 100% packet loss, time 660475ms[/FONT]

yours is probably from your internet provider. Akamai is otherwise in Washington and probably just proxy or some load balancing or something. i don't really know much about networking.

when you get this at the same time try to do:
```
ping www.google.com
```

also see if you can change region in steam. Menu is: Steam --> Settings --> Downloads and then you have on the right *download region*. choose one closest to you or change it to a different one. also try to clear download cache.


but anyway this message you get means you could not connect to steam server. i assume other internet works fine?! is this by any chance a laptop that has wi-fi and wired connection available? i think there is a bug in 20.04 where it would drop the wired connection.

another option is that for some reason firewall is blocking outgoing connection.

Anyway if other connection works fine maybe this should be moved to network part of the forums where people who know more about networks dwell. i would say it is likely not a steam issue.

---

### Post by davoudi on 2021-06-18
> **mastablasta said:**
> i also get akamai.net. but in my case it pings back.
```
[FONT=monospace][COLOR=#000000]ping media.steampowered.com [/COLOR]
PING a1843.b.akamai.net (193.77.14.152) 56(84) bytes of data. 
64 bytes from 193.77.14.152 (193.77.14.152): icmp_seq=1 ttl=61 time=2.05 ms 
64 bytes from 193.77.14.152 (193.77.14.152): icmp_seq=2 ttl=61 time=2.33 ms 
64 bytes from 193.77.14.152 (193.77.14.152): icmp_seq=3 ttl=61 time=2.26 ms 
64 bytes from 193.77.14.152 (193.77.14.152): icmp_seq=4 ttl=61 time=2.34 ms 
64 bytes from 193.77.14.152 (193.77.14.152): icmp_seq=5 ttl=61 time=2.37 ms 
64 bytes from 193.77.14.152 (193.77.14.152): icmp_seq=6 ttl=61 time=2.46 ms 
^C 
--- a1843.b.akamai.net ping statistics --- 
6 packets transmitted, 6 received, 0% packet loss, time 5009ms 
rtt min/avg/max/mdev = 2.055/2.306/2.462/0.129 ms

[/FONT]
```

I checked the IP and it is from my internet provider.

you get: 

yours is probably from your internet provider. Akamai is otherwise in Washington and probably just proxy or some load balancing or something. i don't really know much about networking.

when you get this at the same time try to do:
```
ping www.google.com
```

also see if you can change region in steam. Menu is: Steam --> Settings --> Downloads and then you have on the right *download region*. choose one closest to you or change it to a different one. also try to clear download cache.

 I cannot change the server since steam does not load. It stuck at updating for the first time.

> **mastablasta said:**
> 
but anyway this message you get means you could not connect to steam server. i assume other internet works fine?! is this by any chance a laptop that has wi-fi and wired connection available? i think there is a bug in 20.04 where it would drop the wired connection.

 I also check windows 7 and everything is fine there. So I assume that there is something missing in steam dependency.

> **mastablasta said:**
> 
another option is that for some reason firewall is blocking outgoing connection.

 The firewall is disabled.

> **mastablasta said:**
> 
Anyway if other connection works fine maybe this should be moved to network part of the forums where people who know more about networks dwell. i would say it is likely not a steam issue.

 I will try to do that too.

 Thanks for the reply.

---

### Post by maintech123 on 2021-11-12
I am having exactly the same issue. It will update only so far then stops. I am using 20.10 Mate. I installed Steam with "Software Boutique". I did all the things the others in this post tried. Including multiple install, delete, and install again. I tried synaptic and CLI. I get EXACTLY the same output every time. I tried pinging the listed website but I got nothing. I tried putting the address in my browser. For some reason that worked. Am I missing something? That ping that did work was google. Any answers will be appreciated even if they are wrong. Any helpful answers will be GREATLY appreciated. If there is other info I can include please let me know. Thanks.

---

