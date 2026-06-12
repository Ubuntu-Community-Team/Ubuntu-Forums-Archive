---
title: "Dell Insperon N5010 Wireless problem"
date: 2011-08-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by calicojack42 on 2011-08-10
From Windows to a fully working Ubuntu install in 30 minutes. I LOVE the OS. All of my multifunction keys are working, right down to the one that controls the touchpad. I was glowing when everything and I do mean EVERYTHING worked. I have been working with RHEL servers for many a year, and I am no stranger to how you sometimes "just have to make it work" with Linux OSes and hardware, but this... this blew my hair back.

But...

At random intervals the wireless card will just stop routing packets. Ifconfig shows everything is fine, but I can't ping anything. If I turn off the wireless (via the hot key on the laptop) and turn it back on, I am fine, but eventually it will cut out again. I admit, I am stuck scratching my head over this one. 

Out of curiosity, I just opened a terminal window and started a ping to yahoo. Sure enough, when the wireless paused out, so did the pings... not timed out, they just stopped. 

I'm running Natty Narwhal, and I update religiously. Before posting here, I confirmed that I am currently fully up to date.


Now, here's the clincher: when this happens, and I try to go to a site, it eventually ends up on the TimeWarner search page... TW is our Internet provider. I would chalk this one up to cable issues, but when it happens, other systems not running Linux on my network do not experience any outage at all.

Any thoughts from the community?

---

### Post by calicojack42 on 2011-08-19
Any thoughts of where else I could post this?

---

### Post by calicojack42 on 2011-08-25
Self-bumping out of desperation and lack of shame.

---

### Post by praseodym on 2011-08-25
What encryption do you use? The network-manager often has problems with mixed WPA/WPA2-encryption and therefore loses the connection. Better try pure WPA2-AES (CCMP) if possible. Can you post the following outputs:
```

lspci -nnk | grep -iA2 net
iwconfig
lsmod
iwlist chan
sudo iwlist scan #which Cell is yours?
```

---

### Post by calicojack42 on 2011-09-02
> **praseodym said:**
> What encryption do you use? The network-manager often has problems with mixed WPA/WPA2-encryption and therefore loses the connection. Better try pure WPA2-AES (CCMP) if possible.


I do believe that did it! I have been on without issue. Thanks much for the help.

---

### Post by praseodym on 2011-09-02
You're welcome.

Please mark the post [SOLVED] by editing the first posting left of the title

---

