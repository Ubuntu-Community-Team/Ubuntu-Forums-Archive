---
title: "ethernet problems"
date: 2006-07-23
forum: Desktop Environments
---

### Post by srwilson on 2006-07-23
I just installed 6.06 on a desktop but I'm having a very strange problem getting the ethernet to work.  The only way to make it work is to physically unplug the ethernet cable and plug it back in.  And that makes it work for about a minute then it stops and the light on the switch totally stops blinking.  There is absolutly no activity on the port.  This has worked repeatedly man times as strange as it sounds.

I've isolated it to a software issue.  It is not a hardware issue because it worked perfectly when I booted with a live cd.  The output of ifconfig looks totally fine.  This issue is driving me nuts.  ](*,)   I'm just about to reinstall Ubuntu.  Any other ideas?

---

### Post by rbalfour on 2006-07-23
Can you post the file /etc/network/interfaces

Also, are you using NetworkManager for you networks?

---

### Post by srwilson on 2006-07-23
Here is the /etc/network/interfaces file:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

And no I'm not using network manager.  I would download it if I had internet connectivity.  I'm running a toally stock system with absolutley nothing else installed.

---

### Post by rbalfour on 2006-07-25
sorry for getting back so late. No can you post the output from ifconfig

---

### Post by heathw07 on 2006-07-25
I'm having a somewht similar problem: after upgrading to 6.06, and runnin it for a few days problem free, I went into my router and turned on wireless access. I haven't been able to connect to the network since. Unfortunately I haven't been able to find a step-by-step network setup guide but what I have found is that network -nr is empty (no settings, just titles). When I try to do an add, it says network not reachable and won't let me do it.

BTW, my windows system and VoIP haven't blinked an eye to any changes so I know this is contained to the Linux system.

Any ideas?? :confused:

---

### Post by srwilson on 2006-07-26
Wow, this is one heck of a fix.  I did a fresh install of 5.10 and then used the built-in update manager to upgrade to 6.06.  And it worked!!!  I guess some mysteries are stranger than others.  Thanks for the help.

---

### Post by rbalfour on 2006-07-26
check the /etc/network/interface file 
bet it dosen't look like the one above.

---

