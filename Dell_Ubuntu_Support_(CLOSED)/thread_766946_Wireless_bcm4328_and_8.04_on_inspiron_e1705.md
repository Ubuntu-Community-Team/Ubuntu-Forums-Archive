---
title: "Wireless bcm4328 and 8.04 on inspiron e1705"
date: 2008-04-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by saross0219 on 2008-04-25
Ok I'm sure there are plenty of the same or at least similar issues on this this... BUT here is what I'm finding even after trying fwcutter and ndiswrapper.

lshw shows this:
*-network UNCLAIMED

                description: Network controller

                product: BCM4328 802.11a/b/g/n

                vendor: Broadcom Corporation

                physical id: 0

                bus info: pci@0000:0c:00.0

                version: 01

                width: 64 bits

                clock: 33MHz

                capabilities: bus_master cap_list

                configuration: latency=0


that would be the driver.. thinking the unclaimed is the issue and is therefore going to be the cure on this.

lspci shows:
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)

iwconfig shows:

lo        no wireless extensions.

eth0      no wireless extensions.

I have tried various sites both for the fwcutter and for the ndiswrapper but seems that in my attempts I cant find the driver for ndiswrapper from Windows xp and even dells site doesn't appear to have the right drivers.

ndiswrapper -l shows:
bcmwl5 : invalid driver!
netnwifi : invalid driver!
netw4k32 : invalid driver!
netw4x32 : driver installed
w29n51 : driver installed

that was going by sites and finding dell drivers that "was" the xp drivers for my pc and still got nothing working.  Any sort of help at this point in time would be very very helpful.

---

### Post by qbox on 2008-04-26
[http://ubuntuforums.org/showthread.php?t=297092&highlight=BCM4328](http://ubuntuforums.org/showthread.php?t=297092&highlight=BCM4328)
This worked for me on 7.04
I didnt try it yet on 8.04
I will try soon. Probably will work with new version.

---

### Post by rhul on 2008-05-06
It works for me with Ubuntu 8.04 and a bcm4328 wireless controller in an XPS m1210.  Thank you for the link!

[COLOR="Navy"]I spoke too soon.  I can see wireless networks, but when I try to connect, it won't get past the encryption key.[/COLOR]

---

### Post by rhul on 2008-05-06
Ok, I figured out what the problem was, and I feel kinda dumb.  My network key is 128-bit HEX, but I didn't notice that when the network applet asked for my key that it defaulted the key type to 128-bit pass phrase. After changing it to HEX, it connected fine.

---

### Post by jimjutte on 2008-07-25
I wish mine were so simple. I've literally been trying to tackle this for about a month now.

I can get as far as actually seeing the network, but can't connect. I tried the thread mentioned here and get to the end without errors and unfortunately... nothing.

I have the same system specs listed in the title...

I then tried to use the more up to date version of ndiswrapper... nothing...

For all I know, I'm using the wrong version of driver... I tried the 151517... and then I tried what seemed to be the more correct one 151519 and that seemed to make things worse...

Going a little crazy here now. :(

---

### Post by falcon61102 on 2008-07-25
If you can see the network but cannot connect it may also be due to the security on the network.  You have to manually setup your card to deal with the security.  Run a search for WPA problems or WEP problems in the forum and you should come up with a few threads that may help.  Sorry I can't be more help now, but I'll be on later and can help you out some more.

---

### Post by jimjutte on 2008-07-25
Well, the thing is, I did at one point find I was able to put in the password for my security, in a previous effort, it didn't want to connect... even though it seemed to see it. 

When I completed the instructions here, the network manager was greyed out.

I think it might be as simple as me not understanding two things:

1. the proper driver for my notebook because I don't know with certainty that wireless adapter I have is bcm4328. I know it's a Dell versus an intel and it seems to be the write one but... 

The Notebook itself is Dell Inspiron 9400

2. This is my first crack at Linux in years. At one point I knew a bit about what I was doing... now... I haven't a clue.

So between uncertainty and inexperience, I'm going nowhere fast.

Thanks

---

### Post by falcon61102 on 2008-07-25
I think the first thing you should do is start a new thread because your problem is obviously different than the first poster and that may get some of us confused.  It will also allow more people to see your problem specifically.  

If you start a new thread, post the results of the following two commands:
```
lspci
```
and
```
lshw -C network
```

Those commands will let everyone know exactly what kind of hardware you are dealing with.

Also, you want to post a link to your new thread here so that anyone here can see where you went, that would work great to.

---

