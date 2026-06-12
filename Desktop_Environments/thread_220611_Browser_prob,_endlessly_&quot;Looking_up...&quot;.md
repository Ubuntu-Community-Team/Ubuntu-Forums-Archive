---
title: "Browser prob, endlessly &quot;Looking up...&quot;"
date: 2006-07-21
forum: Desktop Environments
---

### Post by broughcut on 2006-07-21
I find myself hitting refresh a lot in ubuntu, browser frequently stalls when resolving websites, loiters on "Looking up"....  Tried Firefox, Swiftfox and Mozilla. No difference between 'Auto detect proxy' and 'Direct connection'.

Really slows down browsing, very frustrating... esp when posting to forums. :)

It's not down to the internet connection, never have the prob in windows (dual boot). I doubt it has anything to do with wireless, either, the connection is strong and doesn't seem to be missing a beat.

---

### Post by broughcut on 2006-07-21
took about 50 secs for that to post... 'looking up' for about 30 secs,  then 'waiting for ubuntoforums'... /sigh.

---

### Post by neouser99 on 2006-07-21
on the looking up part?? you mean you are having dns issues? how long does it take for gaim or whatever IM client you use to connect to the servers? some stuff you can do on the command line would be ```
$ nslookup google.com
$ nslookup ubuntuforums.org
```
essentially, if the numbers for the pinging are high, like 250ms its a problem with dns. also trying ping some different servers and see what the times are. if all of that still seems ok, try doing a tracepath or mtr or something to ubuntuforums.org and see what is wrong.

-neo

---

### Post by broughcut on 2006-07-21
nslookup google.com
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   google.com
Address: 64.233.187.99
Name:   google.com
Address: 72.14.207.99
Name:   google.com
Address: 64.233.167.99

-- that response is immediate everytime.
 1:  192.168.1.15 (192.168.1.15)        0.274ms pmtu 1500 [has been as high as 1.3]
 1:  192.168.1.1 (192.168.1.1)          2.701ms [7 on one attempt]
 2:  no reply
<snip>
31:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500

same everytime... but google works in the browser. Somtimes it is perfectly responsive, but often I need to hammer links.

---

### Post by neouser99 on 2006-07-21
im sorry, i don't follow, you need to 'hammer' links? also, what is your connection type (cable, dsl)? those replies indicate that your router outside your linksys router probably drops ping requests, so that doesn't tell us much. dns looks ok, your network stuff works b/c you can get to google.com etc. I would say there is the potential that something is up with your ISP, but could be any number of other issues. just as an insanity check, nothing is running 100% cpu or anything is it?

-neo

---

### Post by broughcut on 2006-07-23
click repeatedly, or wait for it to lookup/connect at its leisure.

Not router/ISP related unless linux is somehow a factor. tracert and ping works within Windows.

This has been a consistent problem since I installed Ubuntu a month ago.

---

### Post by Jhongy on 2006-07-23
The two sites you tried nslookup on may have been cached.

I have endless DNS problems. I'm in China, and I think it's my ISP (tried two routers to no avail).

Anyway, I always get extremely long DNS lookups, and regular timeouts if I use the router for DNS, or if DNS is assigned by DHCP. To fix it, I just enter in a fixed IP address and DNS servers into the network settings.

It's a problem I've had to put up with for a few years, and wish it would go away...

---

### Post by broughcut on 2006-07-25
Thanks everyone.

Unless my router or ISP somehow treats Linux traffic differently, this issue is due to a prob within Ubuntu (and is rendering it unusable for net use, unfortunately)... :(

---

### Post by broughcut on 2006-12-30
I'm still having this issue on a clean install of edgy. It effects the other Ubuntu machine using this adsl conection (via a Draytek Vigor switch). Not tried it on another distro. As I've only just made the jump to Ubuntu as a primary OS I've not tested it out on another wifi network, which would be an idea, it would help isolate the problem.

Anyway, Windows on this computer and network has always been perfectly responsive.  

-- that includes the Virtual Machine I'm now running under Ubuntu. :confused: :confused:  I just checked, no probs resolving websites (need windows for Photoshop--running CS3 ok on a 1.2ghz laptop with 750mb RAM, not bad.... why did I mess around tying to get this to work in WINE?).

I have noticed the delay resolving addresses when using apt-get in the term. Once the name resolves everything is fine.... I updated to 6.10 online and then completed a clean PXE install after I ditched windows, both rock steady 170k/s on a 2mb line. It seems to be purely DNS-related.

It seems unlikely to be a problem with Ubuntu's configuration as the issue effects two different laptops (Thinkpad and Panasonic). Is it possible Linux traffic is treated differently by my router or ISP (PlusNet in UK)?

EDIT from VMware: that was 20 secs "Looking up", 3 secs "Waiting" before it posted.. crazy.

EDIT2: Yup. XP is 22.9 secs quicker....


XP on VMWARE:

Microsoft(R) Windows DOS
(C)Copyright Microsoft Corp 1990-2001.

C:\DOCUME~1\BROUGH>tracert bbc.co.uk

Tracing route to bbc.co.uk [212.58.228.155]
over a maximum of 30 hops:

  1     6 ms     2 ms     2 ms  my.router [192.168.1.1]
  2    31 ms    39 ms    30 ms  lo0-plusnet.pte-ag2.plus.net [195.166.128.72]
  3    37 ms    29 ms    28 ms  ge0-0-0-504.pte-gw1.plus.net [84.92.4.90]
  4    29 ms    27 ms    28 ms  ge0-0-0-22.ptn-gw1.plus.net [212.159.4.1]
  5    38 ms    29 ms    28 ms  gi1-1-22.ptn-gw5.plus.net [212.159.4.6]
  6    30 ms    29 ms    30 ms  rt0.thdo.bbc.co.uk [212.58.239.25]
  7    37 ms    29 ms    30 ms  212.58.238.133
  8    29 ms    28 ms    29 ms  212.58.238.36
  9    30 ms    31 ms    32 ms  pos6-0.rt1.mh.bbc.co.uk [212.58.239.254]
 10    28 ms    31 ms    30 ms  virtual0.mh.bbc.co.uk [212.58.228.155]

Trace complete.

...meanwhile, back on the ranch:

brough@broughcut:~$ traceroute bbc.co.uk
traceroute to bbc.co.uk (212.58.228.155), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  1.635 ms  1.696 ms  1.476 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *

[1]+  Stopped                 traceroute bbc.co.uk
brough@broughcut:~$ traceroute bbc.co.uk
traceroute to bbc.co.uk (212.58.228.155), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  1.542 ms  1.518 ms  1.692 ms
 2  * * *
 3  * * *
 4  *
[2]+  Stopped                 traceroute bbc.co.uk
brough@broughcut:~$ tracepath bbc.co.uk
 1:  192.168.1.10 (192.168.1.10)                            0.312ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                              2.734ms 
 2:  no reply
 3:  no reply
 4:  no reply
 5:  no reply
 6:  no reply
 7:  no reply
 8:  no reply
 9:  no reply
10:  no reply
11:  no reply
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500 
brough@broughcut:~$ 

Browsing, it isn't always a problem. In fact, despite the probs with tracepath, bbc.co.uk resolved immediately in Firfox and is working fine with no DNS delays. Very sporadic performance. Btw sorry this was originally posted on the wrong board.

---

### Post by nrKist on 2006-12-31
Have you tried disabling IPv6 yet? I was having the same problem until just recently and that fixed it for me.
```
about:config
```
in the address bar and then search for IPv6. Set *network.dns.disableIPv6* to true. Works in Mozilla, Firefox and SeaMonkey.

I rarely even see "looking up..." "waiting for..." anymore.

---

### Post by broughcut on 2006-12-31
> **nrKist said:**
> Have you tried disabling IPv6 yet? I was having the same problem until just recently and that fixed it for me.
```
about:config
```
in the address bar and then search for IPv6. Set *network.dns.disableIPv6* to true. Works in Mozilla, Firefox and SeaMonkey.

I rarely even see "looking up..." "waiting for..." anymore.

IT WORKS!!! :D 

Thanks a million.

---

