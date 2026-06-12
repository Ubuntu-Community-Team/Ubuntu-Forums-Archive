---
title: "bittorrent problems, probably iptables"
date: 2005-05-16
forum: Desktop Environments
---

### Post by liposuccion on 2005-05-16
Hi. I just installed Kubuntu yesterday.
I installed bittornado with kynaptic, no problems were found.
It opens the torrents, connects to the tracker, etc. but it doesnt connect to any seeds or leeches.
I searched the forum and found this post that explains how to open your ports:
[http://ubuntuforums.org/showthread.php?t=29143](http://ubuntuforums.org/showthread.php?t=29143)

So I tried to make the torrents work by adding a file to my /etc/init.d/ folder. It was called torrentports and this is what it contains:

#! /bin/bash
iptables -t filter -A INPUT -p tcp -m tcp --dport 6881:6889 -j ACCEPT 

So, then I did what the post says:

$chmod +x scriptname $sudo ./scriptname If you want the script to be automaticaly loaded you should put in /etc/init.d by : 
$ sudo cp scriptname /etc/init.d 
now to enable it : 
$sudo update-rc.d scriptname default

This was done returned no problems, so I rebooted my computer. But it still doesnt work, the torrents I open are still not connecting to any seeds nor leeches. 

I tried then tried uninstalling bittornado and installing bittorrent and bitttorrent-gui, also with kynaptic.

I have to mention that from the beginning I uncommented all of the  repositories from the original sources.list and added the Marillat repositories. But I dont think the bittorrent or bittornado packages come from the Marillat repositories though.

If anyone can tell me how to fix this, it would be really appreciated.

---

### Post by liposuccion on 2005-05-16
I just gave up and installed Java and Azureus and it works.
Thanks anyways.  :razz:

---

