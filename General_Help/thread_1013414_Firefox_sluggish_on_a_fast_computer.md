---
title: "Firefox sluggish on a fast computer"
date: 2008-12-16
forum: General Help
---

### Post by oddworld on 2008-12-16
Firefox seems to be sluggish on my laptop in 8.10.
When I have multiple tabs open, everything seems to run slow, especially scrolling and switching tabs.
I am using 32 bit 8.10 with visual effects set to "none".
My computer is pretty fast, Intel Core 2 Duo 2.0 GHZ, 2 Gigs RAM, Intel default display drivers. 
What would be causing this, and is there a workaround?

I don't know if this helps or not, but here is the output of hdparm:

```

davis@davis-laptop:~$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   1570 MB in  2.00 seconds = 784.92 MB/sec
 Timing buffered disk reads:  106 MB in  3.00 seconds =  35.32 MB/sec
davis@davis-laptop:~$ 


```

---

### Post by Izek on 2008-12-16
Run top in terminal or give us a screen of system monitor when this is happening. If you run top, you can tell us what process is taking up the most CPU/etc.

---

### Post by oddworld on 2008-12-16
```


davis@davis-laptop:~$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   1570 MB in  2.00 seconds = 784.92 MB/sec
 Timing buffered disk reads:  106 MB in  3.00 seconds =  35.32 MB/sec
davis@davis-laptop:~$ top

top - 19:49:09 up  2:47,  2 users,  load average: 1.11, 0.74, 0.53
Tasks: 121 total,   1 running, 120 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.6%us,  0.9%sy,  0.0%ni, 91.4%id,  0.9%wa,  0.1%hi,  0.0%si,  0.0%st
Mem:   2063600k total,   835312k used,  1228288k free,    82160k buffers
Swap:  2377580k total,        0k used,  2377580k free,   273160k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5164 root      20   0  300m  29m 9504 S   10  1.5   9:21.66 Xorg               
12960 davis     20   0  2412 1064  800 R    4  0.1   0:00.02 top                
 6731 davis     20   0 21232 8644 7136 S    2  0.4   2:47.65 multiload-apple    
 6810 davis     20   0 11964 2996 1900 S    2  0.1   1:11.33 conky              
 6967 davis     20   0  250m 127m  25m S    2  6.3   6:44.96 firefox            
    1 root      20   0  3056 1884  564 S    0  0.1   0:02.14 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:01.18 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:01.08 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.10 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.08 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.02 khelper            
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
davis@davis-laptop:~$ 


```

---

### Post by oddworld on 2008-12-16
Also, I am using Firefox 3.0.4.
I don't know if that helps anyone with the exact cause of my problem, but I believe it is the most recent. I have been keeping up with all my Ubuntu updates.

---

### Post by albinootje on 2008-12-16
Can you test how slow other browsers perform ?
For example after : 
sudo apt-get install epiphany-browser galeon midori dillo

---

### Post by miniyak on 2008-12-16
how many live feeds do you have? this caused a problem for me before. there not really worth storing anyways, who can read that many... just keep the ones you like. Mozilla should make a warning feature for this.

---

### Post by hikaricore on 2008-12-16
> **miniyak said:**
> how many live feeds do you have? this caused a problem for me before. there not really worth storing anyways, who can read that many... just keep the ones you like. Mozilla should make a warning feature for this.

I highly doubt this is the issue.  I have 15 live feeds I check regularly and read almost every new article in them.  Never noticed a bit of slowdown.

What type of video hardware do you have and did you install the proper drivers for it   This could be part of the issue.

---

### Post by miniyak on 2008-12-16
> **hikaricore said:**
> I highly doubt this is the issue.  I have 15 live feeds I check regularly and read almost every new article in them.  Never noticed a bit of slowdown.

What type of video hardware do you have and did you install the proper drivers for it   This could be part of the issue.

This was on the windows laptop i use i had well over 50 feeds. Firefox sometimes took around 5-10 minutes to load and would sometimes slow down while i was browsing. I could figure out why my browser was slow and every one else's was working fine. till i compared what i was doing with others and decided to trash all the feeds. every things been working fine since and i still keep about 10 feeds. 

another thing could be add-ons but ive heard of people running between 50-100 of them with out a problem...i only run about 7 of them.

regardless,.. if oddworld is using any thing extra, it would help to know, in order to note differences between our systems. Comparing it to other browsers on your system seems to be a good idea. epiphany is a good fall back browser when i need 2 of them. opera didnt come with flash but its cooler than epiphany, any thing will do.

---

### Post by oddworld on 2008-12-16
What is a live feed?

I use Mozilla Firefox with Adblock plus addon and Foxit bookmark sync.

If this helps:
```


davis@davis-laptop:~$ sudo lshw -C display
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
davis@davis-laptop:~$ 


```

---

### Post by oddworld on 2008-12-16
Also, epiphany seems to be a bit quicker and more responsive.
When running firefox the scrolling and tab switching feel as if I am running on a slow machine.
Ideas?

---

### Post by alwayshere on 2008-12-16
I tried this and seemed to help 

> You have to open your /etc/sysctl.conf file.

sudo gedit /etc/sysctl.conf

Scroll to the bottom and just add these lines to it.

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

run the sysctl to take effect.

sudo sysctl -p

but  I think firefox is a bit crappy these days so I would be using "epiphany" or" Konqueror"

I think the problem is to do with dns which I dont fully understand yet 
I tried ns but it made no difference

I find if I use this as my google homepage it is super fast to load as it  a direct address "http://209.85.171.100/"

maybe someone with a few more smarts can help more ?

---

### Post by oddworld on 2008-12-17
That might have helped a little bit, but its hard to tell.
Still slow.

---

### Post by oddworld on 2008-12-17
Is there any way I could update my Intel drivers?
Would that even help?

---

### Post by alwayshere on 2008-12-17
may be the problem is that your modem or your internet itself is the problem
as" epiphany " web browser should be faster and the" [http://209.85.171.100/](http://209.85.171.100/) " page should load up fast as even on firefox so i think you have a hardware or internet server or some crazy deep dark trouble of the unknown??

---

### Post by dcstar on 2008-12-17
Or a search for "disable ipv6" may be of use.

---

### Post by networm1230 on 2008-12-17
look up Firefox tweak aboutconfig  this should help you  [http://codebetter.com/blogs/darrell.norton/archive/2005/01/28/48720.aspx](http://codebetter.com/blogs/darrell.norton/archive/2005/01/28/48720.aspx)

---

### Post by miniyak on 2008-12-17
i think we can safely eliminate feeds or add-ons as being the problem.

as someone who likes to keep things simple, im going to suggest reinstalling firefox. maybe something went wrong in the install, if not at least you can eliminate that as a possible problem.

One more thing id like to add. Its nice that other browsers are slightly faster then firefox, its too bad they dont have add-on support quiet like firefox. once you get used to ad-block and Noscript, all your browsers have to have something like them. Its hard to recommend switching to something else. Particularly if doesn't have add-on support. However i like to keep other browsers around just to see whats out there.

---

### Post by alwayshere on 2008-12-17
> One more thing id like to add. Its nice that other browsers are slightly faster then firefox, its too bad they dont have add-on support quiet like firefox. once you get used to ad-block and Noscript, all your browsers have to have something like them. Its hard to recommend switching to something else. Particularly if doesn't have add-on support. However i like to keep other browsers around just to see whats out there

A big 10/4 on that one I'm gutted that firefox has such bad performance these days even in safe mode basic mode its not as good as it was , as soon as its sorted I'll be going back to it .

---

