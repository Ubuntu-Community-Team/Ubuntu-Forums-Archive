---
title: "Slow Web after installing Linksys router"
date: 2006-04-25
forum: Desktop Environments
---

### Post by dgermann on 2006-04-25
Hi--

Just installed my first router, a Linksys WRT54G Wireless-G.

Ever since, the connections to all Websites seems slow. There is a lot of time spent on "Looking up www.ubuntuforums.org" or whatever Website I am visiting.

My previous set up was a Red Hat 9.0 server which had eth0 connecting with the Internet, and eth1 serving up the Internet to the local network machines. (I replaced that because I think eth0 got fried and Comcast changed my ipaddress, and then nothing worked).

Under gnome I changed the ipaddresses for the gateway and nameservers under  System>Networking. I also edited /etc/network/interfaces, where there were a couple of references to the old gateway and nameserver ipaddresses.

On install of the router, I did update to the latest firmware from Linksys.

I am running Ubuntu 5.10.

Anything else I can do to speed this thing up?

---

### Post by orev on 2006-04-26
That's strange....I am running the same router on an old P4 16ghz box and everything seems to be running great....

I have an Earthlink broadband connection through Time Warner, just plugged in and used after following Linksys Setup.

Everything here is DHCP and auto configured....really very little work.

I am running ubuntu 5.10.

Maybe the trouble is related to the ISP?  (I do have ISP problems on another ubuntu box, but not router related....)

Guess me posting maybe doesn't help much:-k

---

### Post by Blairboy on 2006-04-26
I'd suggest using a different firmware like freeman basic.  It has tons of features and usually clears up a lot of problems.

---

### Post by souki on 2006-04-26
[QUOTE=dgermann]There is a lot of time spent on "Looking up www.ubuntuforums.org" or whatever Website I am visiting.[/QUOTE]

it looks like a dns issue
I have the same problem with the same router, I've tried to flash it (with dd-wrt) but it doesn't solve the issue : dns queries are too slow

even telneting to the router and using nslookup is slow, so I've set up an old pII box to serve dns queries, and now it is really faster

where is your name server : could you post your /etc/resolv.conf ?

---

### Post by twigboy on 2006-04-26
I have that same router as well.  So you had a direct connection before the router?  Also have you tried using a static IP? I would make sure DHCP is working correctly and your DNS address a set up correctly.  Also note that adding a router to any connection will slow it down because of the way the router handles packets.

---

### Post by dgermann on 2006-04-26
orev, Blairboy, souki, and twigboy--

Wow! Thanks for all the help.

Didn't know I could get non-manufacturer firmware. Are there any tricks to getting the right stuff and getting it set up? It toolk the young lady 45 minutes or so to walk me through getting this stuff set up, with a lot of reboots--I took notes, but I doubt I could duplicate it!

I'm pretty sure I don't understand enough about dhcp to do anything with this stuff, but here goes: my set up now is that the isp (Comcast) assigns the ipaddress. I set up something on the router about a cloned MAC address, which I am guessing means that it spoofs the ISP into thinking the router is one of my PCs. But internally, all the computers have hand-assigned ipaddresses--192.168.0.101 through about 120, with some not in use. So I do not know if I have static ipaddresses or not.

Not even sure if that gives you any clues at all.

Here is my resolv.conf file:
```

nameserver 192.168.0.1
nameserver 68.87.72.130
nameserver 68.87.77.130
/etc/resolv.conf (END)

```

Yes, 192.168.0.1 is correct--the tech person who helped me set it up said if my internal addresses were 192.168.0.XXX, this also needed to be a 0 in the third place (do they call that "octal"?).

I did man dd and don't see what your dd -wrt would do. Can you tell me a little more, please, souki?

> 
 I would make sure DHCP is working correctly and your DNS address a set up correctly.


Good idea. How do I go about doing that?

Sign me,

Lost. :confused: 

Thanks, folks!

---

### Post by Eleaf on 2006-04-26
Hello!

I think the problem could also be Ubuntu trying to use some ipv6 stuff and the router isn't liking it.  If so, dns problems can result and sites often don't resolve.

Can you try something?  try pinging something like 'ping www.apple.com' , does it ping okay?
If it pings alright, you will see the ip address of the website, try copying the website's ip into a browser and see if it loads.

dd-wrt is not a linux command, but firmware for the WRT54G [http://www.dd-wrt.com/dd-wrtv2/index.php](http://www.dd-wrt.com/dd-wrtv2/index.php)
Personally, I use hyper-wrt+thybor on my WRT54G, it keeps the same interface while adding many goodies ;).

Good day!

---

### Post by souki on 2006-04-26
dgermann,

try to remove the first entry (nameserver 192.168.0.1)
and see if it speeds up web browsing

if not, try Elaf's tip
there is a specific thread on this [http://www.ubuntuforums.org/showthread.php?t=87798](http://www.ubuntuforums.org/showthread.php?t=87798)
but I don't recommand you to shut off ipv6, try to disable it in firefox before

PS:
Elaf, do you have more links/informations on the firmware you are using ?
thanks

---

### Post by dgermann on 2006-04-27
Eleaf and souki--

Wow! Taking that first entry out, where it was pointed to the router sped things up tremendously.

Now, wanna let me in on the secret? Why did it do that?

Does this tell us there is something to fix in the router setup?

Not sure what doing the ping and browser thing told us, except that neither one seemed faster than the other--perhaps because of all the other busy stuff that was loaded by the apple site.

BTW, here is my ping output. Any idea how to turn off the YP stuff?

```

doug@doug2:~$ ping www.apple.com
YPBINDPROC_DOMAIN: Domain not bound
YPBINDPROC_DOMAIN: Domain not bound
PING www.apple.com.akadns.net (17.254.0.91) 56(84) bytes of data.
YPBINDPROC_DOMAIN: Domain not bound
YPBINDPROC_DOMAIN: Domain not bound
64 bytes from www.apple.com (17.254.0.91): icmp_seq=1 ttl=241 time=65.1 ms

```

Thanks guys! This really sings now! :D

---

### Post by souki on 2006-04-27
yes, there's something wrong with my router's dns too

be aware that if you get your ip with DHCP, your /etc/resolv.conf will be overwritten
you have to setup the routeur to not serve dns queries

for the other problem, the YPBINDPROC thing, this is related to yellow page (NIS)
please, post your /etc/nsswitch.conf here

---

### Post by dgermann on 2006-04-27
souki--

Thanks!

Here's /etc/nsswitch.conf:
```

 /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

# passwd:         ldap files
# group:          ldap files
# shadow:         ldap files
###############
# passwd:         files ldap
# group:          files ldap
# shadow:         files ldap
################
# hosts:          files dns
# networks:       files

# protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
################20060226ddg
# passwd: files nis
# shadow: files nis
# group: files nis
hosts: files nis dns
networks: files nis
protocols: files nis
publickey: nisplus
automount: files nis
# netgroup: files nis
aliases: files nisplus
###################more 20060226ddg
passwd:   compat
group:    compat
shadow:   compat
netgroup: nis
#####################
(END)

```

Also, you said:
> 
be aware that if you get your ip with DHCP, your /etc/resolv.conf will be overwritten
you have to setup the routeur to not serve dns queries


I am guessing that that means that the ISP will overwrite this file if it changes its name servers, might even add back the 192.168.0.1 entry. But I am unclear on how to setup the router not to serve dns queries. How is that done, if you please?

Thanks! You have helped me immensely, souki!

---

### Post by souki on 2006-04-27
for the yello page problem, you have to remove 'nis' from your /etc/nsswitch.conf

here is mine from dapper (backup your file first):
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns mdns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```


for the dns problem, you have to set up your router throught the web interface (I don't recall exactly):

1- open [http://192.168.1.1/](http://192.168.1.1/) in a browser
2- leave login blank and put 'admin' as password
3- on the first? tab (DHCP settings), you should see 3 DNS entries (1. 2. 3.)
change this to have your two DNS entries in 1. and 2.

---

### Post by ronmarley1 on 2006-04-27
[QUOTE=Eleaf]Hello!

I think the problem could also be Ubuntu trying to use some ipv6 stuff and the router isn't liking it.  If so, dns problems can result and sites often don't resolve.

[/QUOTE]
This really helped me with my Linksys router.

---

### Post by dgermann on 2006-04-27
souki--

You are really helpful!

Here is a screenshot of my router control panel, which is where I think you meant. There is only the one ipaddress, which is the one for the router. Does it look like it is OK as is, then, since there are not all three?

I am also wondering if the DHCP server should be set to disable.

As far as the yp stuff is concerned, I replaced my file with yours and tried a ping, and it seems to be working. Any other test I should try to see if the rest of its functionality is as great as you made this?

Thanks, souki, you're tops!

---

### Post by souki on 2006-04-28
looking at your screenshot, in the DHCP Server section,
the last line shows "Static DNS1 : 0.0.0.0"
look at this section, there should be "Static DNS2, Static DNS3"

I think 0.0.0.0 means : "I am the first DNS"
check if DNS2 and DNS3 are "68.87.72.130" and "68.87.77.130"
if so, configure this section to have DNS1=68.87.72.130, DNS2=68.87.77.130

---

### Post by dgermann on 2006-04-28
souki--

You are the expert!

I made the changes you suggested (they were all 0.0.0.0 before I made the changes), and it seems to be working now. Even the tv station sites come up right away now, without a lot of loading time

Thank you, souki!

---

### Post by souki on 2006-04-28
I'm glad this was usefull,
I'm not an expert, I only had the same issue :)

~souki

---

