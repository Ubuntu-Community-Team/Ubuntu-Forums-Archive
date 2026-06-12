---
title: "Deluge/torrent clients seem to kill my network"
date: 2009-01-02
forum: General Help
---

### Post by Jethro_uk on 2009-01-02
Hi all

I run 3 PCs at home, on a nice little network. 2 wireless, 1 wired. I have one PC in the loft (attic) running 24/7, which I use as a torrent/download server. I tend to use Deluge as the client.

I've noticed in the past month or so, that even when deluge is not doing anything, that the performance of the other machines to the internet grinds to a halt. I've proved it by quitting deluge and seeing webpages jump up in browsers.

I'm at a loss as to why this should happen. I've throttled Deluge using the scheduler, but this doesn't appear to be bandwidth related ....

Anyone know what settings I need to look at ?

It also seems to happen with Vuze too, so maybe it's a torrent protocol thing ?

Thanks guys

---

### Post by 2hot6ft2 on 2009-01-02
Perhaps you would be best to ask this in the deluge forum here. [http://forum.deluge-torrent.org/](http://forum.deluge-torrent.org/)
Since I'm sure they know a lot more about any issues with their own torrent client. I found them very helpful even if they're not really fast at responding.

Or at least look and see if anyone else has had that issue and found a solution.

---

### Post by jerome1232 on 2009-01-02
I'm willing to bet (if your behind a router) that your router is running out of sessions which will, depending on your router, lock up network traffic or reboot the router.

(when you say deluge wasn't doing anything was it still seeding?)

There should be options inside the individual torrent clients to limit the number of active connections, which should in turn keep you from maxing your router out.

---

### Post by Jethro_uk on 2009-01-02
Yes, I *am* behind a (cheap) router ... this sounds a promising line of investigation .....

---

### Post by woyzeckswoe on 2009-04-21
this happens to me too.
it worked everithing well with 8.10 but i upgraded on jaunty and now all torrent program break my internet connection i tried disabling upnp and others but it still isnt working, after a couple of hours workin it breaks the connection

did you find a solution?

---

### Post by Blara on 2009-05-05
> **woyzeckswoe said:**
> this happens to me too.
it worked everithing well with 8.10 but i upgraded on jaunty and now all torrent program break my internet connection i tried disabling upnp and others but it still isnt working, after a couple of hours workin it breaks the connection

did you find a solution?

Same problem here, using Ubuntu 8.04. I had no problems in Kubuntu 7.10 when I used that I could download torrents like there was no tomorrow and still surf and the connection would be stable and working. 

I connect directly to the internet (no routers or crap) with a wired connection, and when internet dies I get no indication that the connection is lost, it all seems fine in ifconfig and network manager:confused:

I have no idea what I should post, and any help would be nice :) is there anyway of restarting DHCP through the terminal? it would be a little bit easier than to go through the network manager at least

---

### Post by kpkeerthi on 2009-05-05
Look in Deluge -> Preferences -> Network/Bandwidth and reduce the maximum number of connections to something that your modem/router can handle. In my case, 75 seems to the optimal number. You might have to experiment a bit on this to find out what is optimal for you.

---

### Post by Blara on 2009-05-05
> **kpkeerthi said:**
> Look in Deluge -> Preferences -> Network/Bandwidth and reduce the maximum number of connections to something that your modem/router can handle. In my case, 75 seems to the optimal number. You might have to experiment a bit on this to find out what is optimal for you.

I've tried that in Kubuntu 8.10 when I tried that one out, didn't help any but I'll give it a shot in ubuntu too. and I have NO router or switches

---

### Post by Blara on 2009-05-05
it did no good, I set max connections to 50 and still the connection died. Anyone have any idea where to start looking?

---

### Post by mkvnmtr on 2009-05-05
I have been having problems with Deluge slowing my internet usage on another machine. Seems to be more than before. I have been thinking it is the number of connections but sometimes with few connections it is still slow. I have started to turn Deluge off when I want faster speed with something important. I guess we should try another client to see if this is indeed a problem with Deluge or the router. I tend to think the router.

---

### Post by Blara on 2009-05-05
I had the same problem in ktorrent in kubuntu 8.10 so I doubt it is the client, and I do NOT have a router

---

### Post by rudy.elgato on 2009-05-05
another same problem here...  

whenever deluge is running, my internet connection comes to a complete stop.  I don't even have to be downloading or seeding anything, but as long as deluge itself is running (say, I just have the deluge gui open on my desktop) I'm not able to open a web connection from either the desktop running deluge or from my wireless laptop.  I'm running 8.04 and behind a linksys router.

---

### Post by Jethro_uk on 2009-06-08
Just a wee add on ...

Throughly frustrated, I switched to using Azureus (the pre-vuze version). This seemed to improve things. However for some reason it was unable to d/l torrents from a private tracker I am a member of (no, not porn :-) ). So I switched back to deluge.

As clear as day, I believe there is a memory leak with deluge. It's fine for 24/48 hours, but after than can almost freeze the machine, and I have to SSH in (as NXClient doesn't work) and killall deluge, which immediately frees up everything. Restarting deluge goes fine for the next 24/48 hours.

Luckily I tend to dial in at least once a day to the machine (its in my attic and acts as a download server) so restarting deluge is no big issues (I prefer to quit it nicely and restart it, to avoid it having to check large torrents).

My brother tells me rtorrent is the bees knees, but being a windows kinda guy, I like GUIs and gee-whizz.

---

### Post by Blara on 2009-06-08
Well my problem remains, but I've applied a ugly fix:
I use crontab to load .torrent files from a designated directory into btlaunchmany, which starts at night, and a stop script with killall btlaunchmany. during this time I use another script to restart the network every 15 minutes. It's ugly, but it does get the job done.

btstart.sh:
```

#!/bin/sh
# Start Downloading Torrent Files!
cd
btlaunchmany /path/to/torrents  --minport x --maxport y > torrent.log

```
this stores a log in ~/ that you can check every day to see the progress.

btstop.sh:
```

Killall:
#!/bin/bash
# Stop Downloading ALL Torrent Files!
killall btlaunchmany

```
it just kills btlaunchmany

crontab:
```

# Move .torrent to right directory before BT start
00 02 * * * mv ~/Downloads/*.torrent /path/to/torrentsdownload
# Start BitTorrent Download Script
15 02 * * * sh /path/to/start/script/btstart
# Stop ALL BitTorrent Downloads Script
40 07 * * * sh /path/to/stop/script/btstop

```
first I move all .torrents from my default download dir to my designated torrent dir and then I start btlaunchmany @ 2:15AM and stop it @ 7:40AM. and to keep the torrents downloading I need to do a sudo crontab too, otherwise the connection dies after 10-30minutes after I start btlaunchmany:

sudo crontab:
```

*/15 02-07 * * * /etc/init.d/networking restart
```

---

### Post by conorsulli on 2010-04-01
Is there any other way? Im on Lucid..
Only thing that works is using wine to torrent.
qbittorrent, transmission,deluge all work for the first 5-10 mins with good rates (sometimes 600k).. then the whole thing just crashes outright and none of my computers can connect on the network.

I have used torrents before without any issues with utorrent on windows

also I have lowered all the settings... it still doesn't work

---

### Post by Jive Turkey on 2010-04-01
It might be worth investigating whether your ISP is a known hater of bittorrent.

---

### Post by Cas07 on 2010-04-01
You are posting on a topic that is nearly a year old and based on old versions of Deluge so doubt is relevant to latest 1.2.x releases.

---

