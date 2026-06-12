---
title: "Ktorrent &quot;stalled&quot;"
date: 2006-07-31
forum: Desktop Environments
---

### Post by prophet11 on 2006-07-31
I know this torrent has alot of seeders but it says stalled.. But iN Bitorrnado it doesnt work.. Any suggestions? Anything with my firewall? Other torrent works  though some other ones some work and some dont..

---

### Post by Jucato on 2006-07-31
Torrent downloading can be affected by many factors, AFAIK. So even with many seeders, you still can get stalled. Probably because you are "snubbed" or "choked".

There's also a behavior in KTorrent that I've noticed. When a certain torrent reaches 99.xx% downloaded, it doesn't download anymore until it has uploaded a certain percentage or amount. It think it just want to reinforce the concept of sharing (not leeching). I'm not sure if this is specific to some torrents only, because some torrents download completely without stalling at 99%

---

### Post by prophet11 on 2006-07-31
hasnt even started yet,,,

---

### Post by Jucato on 2006-07-31
Like I said, there are many factors... :(

Have you tried any other torrent client?

I'm guessing that this has something to do with your firewall or some ports. Unfortunately, I know nothing about either... :(

---

### Post by richbarna on 2006-07-31
This happens a lot on ktorrent, don't worry about it.
You get some good torrents and some bad torrents, including bad users that cap their uploads and don't seed.

Remember that everything is free via torrent, and you have to take the rough with the smooth, and hope that there is a seeder at the other end, not a leech.

---

### Post by Oxin on 2006-07-31
I have no experience with Ktorrent but I think I might know what it is. I use Bitlord on Windows and often when I find that a torrent with lots of seeders isn't downloading I find that there's some sort of error message from the tracker site next to the url for the tracker. It seems like certain trackers require you to be a member or something to that effect.

---

### Post by stoeptegel on 2006-08-01
There were some bugs related to this prior to 2.0beta.
AFAIK all known issues with stalling out not affected by the swarm are fixed in the new 2.0RC1 release. 
I would advise to give this newer version a try, it's pretty stable here on my second box.

---

### Post by manu2010 on 2007-07-10
my KTorrent has been dowloading and uploading for almost 3 days and now, suddenly it got stalled. It's not downloading or uploading nothing and the torrent I'm downloading it's not even at the 60%. Does anyone know what to do?
thanks

---

### Post by kelvin spratt on 2007-07-10
your problems are usually due to settings and port forwarding + if your upload settings are to high it will stall
that goes for most applications manually set your upload download speeds to something realistic other wise you will choke your own connection and it will disconnect choose your listening port with care as this also effects connectivity just little tips i picked up.

---

### Post by rillip on 2007-07-10
You may also wish to go to the ktorrent.org site and download the latest version; the one you get from the repos is seriously out of date.

Also, thre could be 10,000 seeders, but if they don't have the one file from the torrent you're waiting to download, nothing happens.  You can seed only part of a torrent if you only downloaded part.

When I upgraded my version, everything started downloading faster, many bugs went away, it was like a brand new program.  I suggest trying that first.

---

### Post by santarulz on 2007-07-10
I get the same problem on Ktorrent. I just press stop and go again, and it resumes w/o a hitch.

---

### Post by mister_p_1998 on 2007-07-13
Dont upgrade to the latest version of Ktorrent if you want to use Bandwidth Scheduler (it stops and starts your downloads on a timed schedule) It doesnt stop on the latest version & you will find its gobbling up all your download quotas (if your ISP imposes one - my allows 30GB a month)

---

### Post by robertc36 on 2007-07-13
Iif all the ports are forwarded and everything is set up- a stalled torrent is a connection to tracker issue.
try to manually announce.
You will see a connection to tracker timeout.
Maybe they are having server problems.
Have you enabled the upnp plugin, if your router is upnp compatible then you do not have too forward ports.
Are you using the default port number, maybe your isp has a block on that.
Trying changing the port number.
Set your upload correctly.
Do not leave upload at unlimited.
There are many reasons why you might be having connection problems but all of them are so easily sorted out.

---

### Post by utylerr on 2008-01-16
Just to chime in on this thread, I was experiencing frequent stalling in ktorrent, resolved as follows:

1. Stalling at startup: this appeared to be due to the tracker being temporarily unavailable. A few hours later the tracker came back up and things started working.

2. Stalling after 2-4 hours of operation; my line went dead and I was unable to connect to the net. I traced this problem to my linksys BEFSR41 router, which was freezing up. Reducing the number of simultaneous connections allowed by ktorrent appears to have resolved this issue; thus I assume that the linksys was having problems maintaining the default 800 connections. I cut the number in half (to 400) and so far no problems.

---

