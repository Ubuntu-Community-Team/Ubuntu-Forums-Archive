---
title: "BitTorrent Box"
date: 2008-12-07
forum: General Help
---

### Post by championchap on 2008-12-07
Howdy guys, I'm looking to set up a BitTorrent box in my Uni house to stop the bandwidth getting totally raped by 5 active torrent users trying to download all at once.

I'm liking the look of Deluge a lot, love the idea of a web interface.

I'm looking to buy some cheap hardware, ive already got a hard drive and a GB of RAM and to load it up with one of the 'buntus - At the moment, i'm thinking XUbuntu?

Anyway, i'm in need of a bit of help, i've used Ubuntu a bit and I don't fear the terminal exactly.. but some guidance is required. 

Also, it looks like i'm going to need to plug a wifi card into the box as nobody wants a cable runnign from the router.. :/
Any suggestions on a good one? I've had pleanty of Ubuntu/wifi headaches in the past which i'd like to avoid if possible.

Thanks in advance!

---

### Post by MedianMajik on 2008-12-07
Here is a great [reference]("http://filesharingtalk.com/vb3/f-seedbox-discussion-154/t-naqs-complete-setup-guide-linux-seedboxes-fedora-corecentosdebianubuntu-281331") for creating your own seedbox.  It doesn't talk directly about Ubuntu as much, but it should answer some of your questions.  You really don't need much to have a fully functioning seedbox besides at least 256mb of ram (I'd go for at least 512mb).  

You'll want to set up a static IP address and enable [port forwarding]("http://portforward.com/") on your router.  Be sure to use a port that is not standard (aka 6889 range) because your isp is most likely already throttling it.

I personally use Deluge and it has a very nice web ui.  I also recommend using uTorrent via Wine (it is my favorite way to create torrents and makes a good backup since it is so common).  All of the *nix clients I'm aware of have a webu ui (Transmission, rTorrent, kTorrent, qTorrent, etc).

I also recommend an ipblocker such as moblock (cli) or ipblock (java).  Peerguardian makes one as well, but it doesn't seem to get nearly as many updates as their Windows version (someone correct me if I'm wrong).  Unless you're on private trackers your torrent activity is being noticed somewhere 8-[

Always configure your client to encrypt all data.  If you must use public trackers [BitChe]("http://www.convivea.com/") is easily the best way to search for anything (it can be run via Wine).

Your best bet is to run the seedbox headless (save those monitors) and configure ftp/rss feeds to allow everyone to retrieve their files/download notifications over your network.

---

### Post by championchap on 2008-12-07
Thanks a lot, I'm not a big user of public trackers though and my ISP provided me with a static IP when i signed up to them :)

I was thinking about just using VNC to get into the seedbox but i'm a little confused about Networking Windows/Mac to Linux Boxes.
I hear a lot about Samba?

Anyway, what i was thinking is rather than go to the trouble of setting up an RSS feed (i'm not a fan :O) or anything wouldn't i be able to just share the folder that the downloads are going to on the network?

---

### Post by MedianMajik on 2008-12-07
Yep, VNC works great.  Sharing folders is fine.  FTP just helps if you are away from home.  I don't know about Windows, but my roommates use macs and we never have problems networking together.

---

### Post by championchap on 2008-12-07
Ahh good stuff, i have no plans to access this over the net or anything anyway.

Is there anywhere that gives a list of wireless cards that play nice with Ubuntu?

---

### Post by MedianMajik on 2008-12-07
[Ask]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking") and [you]("http://linuxwireless.org/en/users/Devices") shall [receive]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported").

---

