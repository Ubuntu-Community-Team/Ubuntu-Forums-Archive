---
title: "Ubuntu Forum Won't Load"
date: 2006-11-29
forum: Forum Feedback &amp; Help
---

### Post by Paul41 on 2006-11-29
This weekend I started having a problem where the Ubuntu forums won't load on my home computer. When I try to go to the forums it just keeps trying to load the page and eventually times out. This is the only site that I am not able to load and have never had any problem until this weekend. I didn't install anything new or make any changes. I tried to ping the site and that worked. I am at my work computer now and don't have any problems here.

I tried to clear my cache but that didn't help. I am stumped. Does anyone have any idea what the problem could be?

---

### Post by Paul41 on 2006-12-01
I am still having this problem and had no success in figuring out what it could be. Here is what I have tried up until now:

1. I use Firefox so I tried using Opera to see if that made a difference, but no luck.

2. I tried using Lynx to see if it was just some kind of graphical problem. The forums wouldn't load here either.

3. I have windows on VMWare so I tried that with IE and Firefox, but neither worked.

4. Tried to disable IPv6 in Firefox. This also didn't make any difference.

I have found that if I get lucky and I am willing to keep repeatadly restarting my browser I can get pages on the forums. Each time I restart the browser I get a little more of the page loaded. Just refreshing the page doesn't seam to work, I have to completely restart the browser.

I would really like to be able to get back into the forums at home. This is where I use Ubuntu so that is where I need it the most ](*,) . Also, I can't try to help other people if I can't get to the forum :) .

---

### Post by KiwiNZ on 2006-12-01
Do you have a Firewall?
 
If so try turning it off and see if this makes a difference

---

### Post by Paul41 on 2006-12-01
> Do you have a Firewall?

I do have a firewall. The weird thing is that I have always been able to get to the site before (even with the firewall). This is just something that started all of the sudden. I will try to turn it off though just to make sure.

---

### Post by Paul41 on 2006-12-01
OK, I tried to turn the firewall and that didn't help either. Any more ideas?

---

### Post by KiwiNZ on 2006-12-01
That is truely strange, can you do a tracert and post the result ?

---

### Post by Paul41 on 2006-12-01
Here is the result of the traceroute

> traceroute to ubuntuforums.org (82.211.81.186), 30 hops max, 40 byte packets
 1  * * *
 2  10.96.0.1 (10.96.0.1)  7.549 ms  6.677 ms  5.859 ms
 3  gig2 (24.28.229.153)  6.345 ms  8.287 ms *
 4  srp12 (24.28.224.172)  21.746 ms  9.597 ms  8.477 ms
 5  srp0 (24.28.226.196)  12.532 ms  11.058 ms *
 6  son4 (24.93.64.73)  14.009 ms  12.549 ms  11.489 ms
 7  tenge (4.71.160.1)  12.963 ms tenge-1-3.car1.Raleigh1.Level3.net (4.71.160.5)  13.257 ms *
 8  ae (4.69.132.174)  15.301 ms  11.697 ms  15.951 ms
 9  ae (4.69.132.178)  18.143 ms  28.823 ms  18.475 ms
10  ae (4.69.132.114)  103.298 ms  104.758 ms  108.225 ms
11  ae (4.69.133.81)  99.569 ms  103.364 ms  107.602 ms
12  ae (4.69.133.94)  107.130 ms  105.418 ms *
13  ge-3-0-0-51.gar1.London2.Level3.net (4.68.117.11)  108.817 ms ge-3-0-0-53.gar1.London2.Level3.net (4.68.117.75)  99.791 ms ge (4.68.117.139)  99.413 ms
14  195.50.91.150 (195.50.91.150)  97.899 ms * ge-6-1.core-r-1.lon2.mnet.net.uk (195.50.91.134)  107.537 ms
15  * vlan102.core (62.140.218.201)  103.375 ms  101.217 ms
16  * 85.133.32.130 (85.133.32.130)  106.952 ms  107.042 ms
17  82.211.81.76 (82.211.81.76)  107.254 ms  106.797 ms  106.574 ms
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

---

### Post by KiwiNZ on 2006-12-01
Its timing out at the very last hop

 16   324 ms   323 ms   328 ms  85.133.32.130
 17   330 ms   326 ms   325 ms  82.211.81.76
 18   327 ms   330 ms   324 ms  ubuntuforums.org [82.211.81.186]
 
Trace complete.
 
If you put the UF ip address 82.211.81.186 into the browser can you connect?

---

### Post by Paul41 on 2006-12-02
Same problem when I try to use the ip. I also ran a traceroute on the ip and it times out in the same place.

---

### Post by ubuntu-geek on 2006-12-03
Just out of curiosity does it work now?

---

### Post by Paul41 on 2006-12-03
> Just out of curiosity does it work now?

Unfortunately no. I am still having the same problem with both the domain name and the ip both.

---

### Post by KiwiNZ on 2006-12-03
Can you please PM me the IP address for the PC in question and your service providors IP

---

### Post by grantw on 2006-12-03
I'm experiencing the exact problem as described by Paul41.  However, I just installed Ubuntu 6.10, so I cannot state that I've ever successfully gotten the forums pages to load in my browser on the Ubuntu box.  The very bizarre (and infuriating) factor is that I can get to ubuntuforums.org on my Win XP laptop connected via the same LAN.  To make this clear:

Ubuntu 6.10 is on 192.168.1.2 on my LAN.  From here, I can't reach ubuntuforums.org as described by Paul41.

(I've turned off Firestarter firewall on the Ubuntu box and it makes no difference.)

WinXP is on 192.168.1.6 on my LAN.  No problem reaching ubuntuforums.org. (This is the machine I'm posting from now)

I have traceroute output for both of these machines.  I'll PM them to KiwiNZ along with the info he requested.

---

### Post by ubuntu-geek on 2006-12-03
> **grantw said:**
> I'm experiencing the exact problem as described by Paul41.  However, I just installed Ubuntu 6.10, so I cannot state that I've ever successfully gotten the forums pages to load in my browser on the Ubuntu box.  The very bizarre (and infuriating) factor is that I can get to ubuntuforums.org on my Win XP laptop connected via the same LAN.  To make this clear:

Ubuntu 6.10 is on 192.168.1.2 on my LAN.  From here, I can't reach ubuntuforums.org as described by Paul41.

(I've turned off Firestarter firewall on the Ubuntu box and it makes no difference.)

WinXP is on 192.168.1.6 on my LAN.  No problem reaching ubuntuforums.org. (This is the machine I'm posting from now)

I have traceroute output for both of these machines.  I'll PM them to KiwiNZ along with the info he requested.
Interesting indeed... You cannot access the site via the ip address either? [http://82.211.81.186](http://82.211.81.186)

---

### Post by KiwiNZ on 2006-12-03
U-G I have checked the IP's against the list of blocked IP's , no match

---

### Post by ubuntu-geek on 2006-12-03
> **KiwiNZ said:**
> U-G I have checked the IP's against the list of blocked IP's , no match
Same here and there are no ip's hard blocked on the server..

---

### Post by grantw on 2006-12-04
Tried the IP address in the browser.  That doesn't work either. 

Obviously my IP couldn't be blocked, since I have 2 PCs coming from the same external IP address and one (the WinXP box) can display ubuntuforums.org, but the other (the Ubuntu box) cannot.  Whatever the problem is, it's on my Ubuntu box.  This is really maddening - using a Windows machine on my local LAN to get info on the ubuntuforums.org page because the Ubuntu box can't view it.

I haven't encountered any other URLs that are giving me problems on Ubuntu, only ubuntuforums.org.  Sometimes it will display the top banner of the forums pages, but then Firefox (or Opera, tried both, makes no difference) just churns away as if it is trying really hard to load the rest of the content.  I move over to the Windows box and hit ubuntuforums.org at exactly the same time and it displays without a problem.

---

### Post by KiwiNZ on 2006-12-04
Try 
 
you can add that command to execute whenever the card comes up (without the sudo prefix, but add a pre-up or up prefix) to /etc/network/interfaces ... so it will look like this:

.
.
.
auto eth0
iface eth0 inet dhcp
pre-up ifconfig eth0 mtu 1450

---

### Post by grantw on 2006-12-05
That certainly seems to have done the trick, since I am posting this reply via my Ubuntu box now.  Thanks very much. 

Not to continue complaining, but the responsiveness of the forum page is quite slow (but I'm glad to finally be seeing it at all).  Would you suggest that I drop that MTU even lower to see if it helps?

---

### Post by Paul41 on 2006-12-05
> Try

you can add that command to execute whenever the card comes up (without the sudo prefix, but add a pre-up or up prefix) to /etc/network/interfaces ... so it will look like this:

.
.
.
auto eth0
iface eth0 inet dhcp
pre-up ifconfig eth0 mtu 1450

When I tried this I lost my network connection completely. Did I do this right?

I opened /etc/network/interfaces and added the auto eth0 ... lines to the bottom of the file. When I restarted I didn't have any network connection at all.

---

### Post by Paul41 on 2006-12-05
Edit: Deleted because this was an accidental double post.

---

### Post by grantw on 2006-12-05
The first two lines were probably already in your interfaces file:

auto eth0
iface eth0 inet dhcp

So you only need to add this one:

pre-up ifconfig eth0 mtu 1450

Perhaps double-check your interfaces file?  I didn't have a problem.

Although this change to MTU has managed to get me into the forums on my Ubuntu browser, the performance is terrible.  Sometimes the forum pages still don't load up or take forever to load.  It's bizarre to me that I have to change my MTU from the default of 1500 (which is exactly what it is set to on the functioning WinXP box) to make my Ubuntu box get to ubuntuforums.org.

---

### Post by ubuntu-geek on 2006-12-05
Hmm interesting you both are from NC.. What ISP's do you use?

---

### Post by grantw on 2006-12-05
I'm on Time-Warner Cable Roadrunner in Raleigh.

---

### Post by horace on 2006-12-05
I've had the same problem connecting to all the Ubuntu sites in this IP range and also had to use the MTU fix to get round it - but that is with a UK ISP, and no other sites were affected in my experience. Suggests to me that it may not be the ISP but something at the Ubuntu host end?

---

### Post by Paul41 on 2006-12-05
Adding pre-up ifconfig eth0 mtu 1450 only made it so my network connection did not die, but I am still having problems on the forum.

Even before making this change, if I am very patient and willing to keep trying to get a page to load in the forum to load it will. The problem is that it takes me about 30 minutes of trying before it happens.

I am also on Time Warner's Road Runner, but in Greensboro.

---

### Post by Paul41 on 2006-12-07
Does anyone have any more information on what could be going on here?

---

### Post by grantw on 2006-12-08
Unfortunately I haven't heard anymore about it either Paul41, but the ubuntuforums.org page does seem to be performing better for me today.  Not coincidentally, I've also noticed a problem in the past with connecting to the archive.canonical.com repository.  It sometimes timeouts on this repository during an apt-get update command.  I noticed that ubuntuforums.org is 82.211.81.186 and archive.canonical.com is 82.211.81.142, so I'm sure there's a connection there.

---

### Post by Paul41 on 2006-12-08
It seems like this problem has magically fixed itself. I don't know what changed (I didn't make any changes), but hopefully it stays fixed :) .

---

### Post by ubuntu-geek on 2006-12-08
We didnt change anything on our server. My only guess would be that something in the routing tables of various isps got solved. Our servers are located in the UK, every once in awhile i notice a slow response from here in the usa but nothing major.

/shrug.. 

at least its working now.

---

