---
title: "Transmission and Deluge"
date: 2009-06-17
forum: General Help
---

### Post by punkbohemian on 2009-06-17
I have been using Transmission for quite a while, but I've been getting some really lousy transfer rates ranging from 5kb to just idle. Based on what I read on the boards here, Deluge comes highly recommended over Transmission, so I dl'd it and started it up. It worked great, for about 10 minutes, and now my transfer rates have bottomed out there, too. When I look at my connected peers, many of them have the full file. On one of them, I'm the one of two peers who don't have the full file (everyone else has 100%). I know it's possible that some folks just aren't seeding, but I'm seeing way too many peers with 100% to think that this is the case.

I really don't know much about torrents/file sharing, so I have no idea what's going on here. I'd appreciate any help on this. Thanks.

---

### Post by prem1er on 2009-06-17
Are the ports on your router/firewall opened to allow connections?

---

### Post by martin_legion on 2009-06-17
As prem1er says, check the ports are open on your router.
You can also see if disabling protocol encryption (I don't remember if it's called that way), or if enabled, allow to recieve un-encrypted connections.
You could also try downloading some very popular torrent, just to see if it's a configuration problem or just that the torrent you want to download has few/no seeds.

---

### Post by lovinglinux on 2009-06-17
Please answer these questions:

[list][*] is the port opened in the router?
[*] what is the total number of seeders and peers for this particular torrent?
[*] how many peers you are connected to?
[*] what is your share ratio?
[*] what is your upload speed?
[*] what is your upload speed limit imposed by the ISP?
[*] what is your upload speed limit configured in Deluge?
[*] what is the status of the tracker?
[*] are you using the blocklist plugin?
[*] are you using an ip blocker like moblock or iplist?
[*] do you have firewall rules enabled?
[*] what happens if you try to download a popular torrent like an [Ubuntu release](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)?[/list]

---

### Post by punkbohemian on 2009-06-18
*  is the port opened in the router?

I assume so? How do I verify this?

    * what is the total number of seeders and peers for this particular torrent?

It ranges, I get fewer all around from transmission (1 or 2 seeders, 15-25 peers). With Deluge it's like 10-20 seeders and 15-25 peers)

    * how many peers you are connected to?

15-25

    * what is your share ratio?

Probably only around .3, but I can't share what I don't have. I don't see what this has to do with it, though. I asked some time ago (on another board) if there was some kind of control for leechers (I was miffed about not enough seeders for various torrents), and everyone said that the ratio was basically only for the user's benefit.

    * what is your upload speed?

It depends, My actual ranges from 5-25kbps.

    * what is your upload speed limit imposed by the ISP?

I don't know.

    * what is your upload speed limit configured in Deluge?

5-25kbps

    * what is the status of the tracker?

Either downloading, or idle.

    * are you using the blocklist plugin?

I don't know what that is.

    * are you using an ip blocker like moblock or iplist?

Not that I know of.

    * do you have firewall rules enabled?

Not that I know of.

    * what happens if you try to download a popular torrent like an Ubuntu release?

The same. Once in a long while, with really popular torrents, I'll get transfer rates of 50500kbps, but it's only ever for a short burst.

---

### Post by prem1er on 2009-06-18
Sounds like the router may be part of the problem.  You need to forward the port you use for your torrent client.  This allows connections to be made and kept without being filtered by the routers firewall.  Follow the instructions on this page (for your router).

[http://portforward.com/](http://portforward.com/)

---

### Post by lovinglinux on 2009-06-18
> **punkbohemian said:**
> *  is the port opened in the router?

I assume so? How do I verify this?


If you are not sure, then probably the port is closed, which will not prevent downloading, but will reduce the number or connected peers and thus the speed.

Port forwarding depends on your router. Check [http://portforward.com/](http://portforward.com/)


> **punkbohemian said:**
> 

    * what is the total number of seeders and peers for this particular torrent?

It ranges, I get fewer all around from transmission (1 or 2 seeders, 15-25 peers). With Deluge it's like 10-20 seeders and 15-25 peers)

The total number of peers is low and the seed/peer ratio is not good. This definitely has an impact on your speed. Healthy torrents usually have a few hundred to thousands of peers and a seed/peer ratio of at least 1:1.

> **punkbohemian said:**
> 

    * how many peers you are connected to?

15-25

It seems that you don't have connection problems. I think the real issue is the number of available peers and their upload speeds. Try finding similar torrents with more seeders and peers.

> **punkbohemian said:**
> 
    * what is your share ratio?

Probably only around .3, but I can't share what I don't have. I don't see what this has to do with it, though. I asked some time ago (on another board) if there was some kind of control for leechers (I was miffed about not enough seeders for various torrents), and everyone said that the ratio was basically only for the user's benefit.

Depends on the tracker and on the torrent client, but as a general rule, the more you give the more you get. When you start a torrent you don't have any pieces to share, so your share ratio is low and thus your download speed will be also slow. Once you get some pieces and start to share them, your download speed will improve. That's why torrents are slower in the beginning and faster at the end. You must give some time to let the speed improve.

> **punkbohemian said:**
> 

    * what is your upload speed?

It depends, My actual ranges from 5-25kbps.

    * what is your upload speed limit imposed by the ISP?

I don't know.

    * what is your upload speed limit configured in Deluge?

5-25kbps

It is a slow upload speed. As I said, the more you give, the more you get. If you have slow upload speeds your download speed will be reduced, even if you have available download bandwidth. You should check the upload limit of your connection ([http://www.speedtest.net](http://www.speedtest.net)) then set the upload limit on the torrent client to 80% of that speed. If you use unlimited upload speed it might slow down your download too.

> **punkbohemian said:**
> 

    * what is the status of the tracker?

Either downloading, or idle.



You are confusing the status of the tracker with the status of the torrent.

You you start a torrent (downloading), the torrent client needs to connect to a tracker to get the list of peers. If the tracker is down, then you won't be able to get the peers IPs and won't be able to connect to them. The tracker status is usually "OK" or it gives an error. An error usually means the tracker is down or couldn't be reached for some reason. Nevertheless, I think this is not the problem in your case.

> **punkbohemian said:**
> 

    * are you using the blocklist plugin?

I don't know what that is.

It is a feature that uses a list of known bad IPs and prevent them to connect to you. If you have it enable, then you will connect to less peers than the number available. With healthy torrents, this helps to prevent peers with fake files to upload to you, thus reducing the time need to download a torrent. It is also used as a security tool, depending on which IP lists you use. This is not enabled by default on Deluge, but I'm not sure about Transmission. Check the "Peers" tab in Transmission preferences and uncheck the blocklist option.

> **punkbohemian said:**
> 

    * are you using an ip blocker like moblock or iplist?

Not that I know of.

    * do you have firewall rules enabled?

Not that I know of.

Since you don't know, then you are probably not using them. The firewall allows all traffic by default and the ip blockers are not installed by default. 

> **punkbohemian said:**
> 

    * what happens if you try to download a popular torrent like an Ubuntu release?

The same. Once in a long while, with really popular torrents, I'll get transfer rates of 50500kbps, but it's only ever for a short burst.

This is a little bit odd. Please post a screen shot of your test on [http://www.speedtest.net](http://www.speedtest.net)

I think the problem might be the health of the torrents and probably the port on your router. I consider a good torrent those with a seed/peer ratio of at least 2:1 and more than 500 peers. Nevertheless, speed can be very high on a torrent with just a dozen of peers, if you are lucky enough to connect to someone with high upload speeds. In the other hand it can be slow in swarms with hundreds of peers. The speed of a single peer download depends on it's upload limit, the number of torrents it is sharing and the number of upload slots it uses.

---

### Post by abyrne on 2009-06-18
I've had this problem before. The problem was in my computer's firewall and my router. In my router, I set up port forwarding (using the port that Transmission uses, check the settings for this). In my computer's firewall, using firestarter, I just stopped it while I was using Transmission. I'm not going into details due to the differences in routers. So someone feel free to explain how to do this:KS

---

### Post by hibliss on 2009-06-18
To reinforce some points here, any client that follows the protocol properly is going to achieve similar speeds. 

Swarms will vary as discussed based on seeder/leecher ratio.

If you have an open port to exchange data, the number of up/down slots properly set per torrent, the number of active torrents properly limited, and your upload speed capped at 80% of it's potential, then you should get optimal speeds for that swarm.

Transmission does fine for me, so does Deluge, but I prefer rtorrent/libtorrent.

The main thing that has to be kept in mind with bittorrent, especially on public trackers is that people cap their speeds and don't seed back. You are not downloading from a 100mbit server most of the time, and P2P is not going to be the fastest method many times.

---

### Post by lovinglinux on 2009-06-21
> **SPARTAN-118 said:**
> My downloads usually are very quick to begin with (for example, a file that was 1.7 GB had 18% done in around 2 mins.), but after that quick burst, become idle.

That burst is probably due to a extremely high bandwidth uploader. It happens sometimes, specially when there are some Japanese seeders on the swarm. If you are lucky enough to stay connected to this peer through the end, it will download really fast, but this is not usually the case.

> **SPARTAN-118 said:**
> The port Transmission is "listening" to is **closed**, and I am very hesitant to open or forward it, since last time I did that on my dad's computer, we lost internet for a week or two.

Opening the port should not cause any damage to your connection. I guess the problem is that you have overloaded the router with torrent traffic. This can slow down other Internet activities and sometimes crash the router.

> **SPARTAN-118 said:**
> The tracker website (*link removed*) says that there are 15 seeds and 9 peers, but the download just becomes idle anyway. (Transmission also says that, while it is downloading, there are only 4 peers. Don't know about seeders, though.)

That is a really bad torrent. The seed/leecher ratio is good, but 24 peers is very low. Keep in mind that the peers from this torrent might be downloading and seeding several other torrents, so their bandwidth is shared among all torrents each one is sharing.

Additionally, the number of seeders/peers on those site are update only couple of hours per day, so they do not necessarily represent the real number. Besides, old torrents are not even updated. Did you noticed that it was updated 20 days ago?

Please don't post link to torrents if you don't have legal rights to distribute it.

> **SPARTAN-118 said:**
> Is there a way to forward our router w/o losing internet again? Yes, I used the instructions at [www.portforward.com/]("http://www.portforward.com/") but that's what caused the screw-up.

I have a Toshiba Satellite a200 Series laptop, and our router is a 2-Wire (meaning modem AND router in one device) Bell. The router that got screwed up was a D-Link, so I'm not sure if we would have the same problem.

There is only one way to do it. I doubt it was responsible for your Internet loss, but there isn't enough information to pinpoint the culprit.

---

### Post by RobOrr on 2009-06-21
it might also be worth checking if your ISP throttles certain internet traffic, such as torrent traffic, mine certainly gets capped between, 6pm and 11pm. Then again, from your description of the problem it sounds like port forwarding hasn't been sorted out properly. The portforward website has all the info you need on it, best of luck.

---

