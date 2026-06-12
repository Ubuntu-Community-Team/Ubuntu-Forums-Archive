---
title: "Are there Differences in Download Speeds? Is Ktorrent Slower than Most/Others?"
date: 2008-12-08
forum: General Help
---

### Post by OzzyFrank on 2008-12-08
OK, now I've seen quite a few posts regarding some bittorrent clients in Ubuntu being slower than others (Ktorrent is often mentioned). I always took them with a grain of salt, and put down speed differences to just plain luck (you know, available bandwidth at the time... unfortunately picking downloads with few seeders, that sort of thing). But some people were quite adamant that it wasn't just a case of luck. And now I am on the verge of agreeing with them.

I decided the only real way of testing this was to load the same torrents in Ktorrent/Ubuntu and Bitlord/Windows and compare. So I loaded up 3 new torrents in Ktorrent and they never even registered any seeders (or leechers) online... but a 5 minute reboot into Windows, load those up, and away go the downloads instantly!

So... dare I ask... is there something amiss with how Ktorrent does things? Or does this affect all bittorrent clients in Ubuntu... or was my little test just another sign of "good/bad timing" and "luck of the draw"?? As I said, my sense of logic said beforehand that this must be the case with others, but now I admit there could be all sorts of technical issues I am unaware or even understand. I'd like to hear what others say on this.

Oh, and if the answer is something like "Oh, Ktorrent is infamous for this because of <INSERT TECHNICAL JARGON HERE>", please let me know of an app that isn't affected. From where I am standing, it seems Bitlord is making Ktorrent look pretty pathetic. And I don't have any limits imposed on Ktorrent, so doubt that is a factor between the two. Cheers. Frank

---

### Post by tvtech on 2008-12-08
it's like anything you have to configure it Tranmission is one of the easier bit torrent clients for nix.  azurues runs the same in nix and windows, you need a lot of configurating in both.  I never had a problem with Ktorrent, but it was a little bit configuration intensive.  

the best way to check is to run ktorrent up against transmission, and azureus in linux to see if there is any tangable difference. But there shouldn't be. 

and your right SOYLENT GREEN IS PEOPLE!!!!!!!!!!!!!

---

### Post by binbash on 2008-12-08
I am using ktorrent right now and speed is same with deluge.I am getting max speed for both

---

### Post by OzzyFrank on 2008-12-08
What did you have to configure? You mean just things like lowering the amount of seeding so you're not giving away more than you're getting? I've checked all that (to the best of my knowledge) since Ktorrent was updated with the Ubuntu 8.10 upgrade (and move to KDE4, as I have KDE as well as Gnome).

Are there any specific settings that I should be looking at? Especially things that could have been reset with the upgrade and I never noticed? I only ever checked the seeding ratio, and that was how I left it.

As I said, added 3 new torrents in KTorrent and never even got to the stage of showing me how many people were connected (and I did also stop and start them to see if it made a difference). But 5 mins later in Windows and up pop the seeders and leechers instantly, and within a few seconds am downloading them.

---

### Post by OzzyFrank on 2008-12-14
Oh boy... from where I am sitting, there is a HUGE difference in download speeds! And I am telling you, I have tried to configure Ktorrent every which way, and all it ever really seems to do is either (a) nothing or (b) increase upload/seeding speeds. Sometimes it looks hopeful, then the downloads drop to basically a trickle if that. A torrent can have a bunch of 100% seeders yet I get nothing from them... while in Windows/Bitlord this isn't the case. But to be sure it isn't just luck of the draw I decided to install Azureus/Vuze and compare with a torrent that I am barely getting any movement on.

So, using a vid of the 1964 FA Cup (go West Ham!) as an example, my results are as follows. The torrent only has a handful of seeders, but all at 100%. Of the 1.46Gb I have only gotten 1.11% (16.6Mb) in the last few days. Here and there the torrent starts and might go for a little while, then drops back to nothing (with the 100% seeders just sitting there looking at me). I just tried again up until loading Vuze, and got not a single byte all morning. Kept stopping and restarting... nothing.

Load the torrent into Vuze, and immediately it starts using about a third or more of my bandwidth (on ADSL that's 10kps which is a lot better than 1kps in Ktorrrent, when I am getting anything at all that is).

So, while it has taken me literally days to get 16.6Mb from this torrent, in Vuze I have already gotten 8.5Mb just while typing this!!!

So, logic says something has to be up with Ktorrent, or the way it is set up (though as I said, I have played around with settings quite a lot). In a few minutes, Vuze will have caught up with and surpassed what was downloaded over a few days using Ktorrent... so I guess I have answered my own question.

Pity about Ktorrent, as I really liked it, but watching it wasting my download time like this is just too painful - at times, all downloads combined can be less than 1Kps, which just doesn't happen in other clients unless I have picked some downloads with barely any seeders. If someone knows any info that might help, like perhaps alternative ports to the default ones Ktorrent uses, or anything that could help, please post it here for others to read. Personally, I think it's just time to give up on Ktorrent. I never was going to bother with Vuze, but glad I did!

---

### Post by OzzyFrank on 2008-12-14
PS: I did just try again with Ktorrent, and after finding the seeders did nothing else. Restarting it in Vuze it is using over half my bandwidth and has now overtaken what was downloaded in days using Ktorrent.

---

### Post by amdalex on 2008-12-14
I use Frostwire for P2P and torrents. It will use all of my bandwidth if you don't cap it. Does anyone else like frostwire?

---

### Post by OzzyFrank on 2008-12-15
I might give **Frostwire** a shot, even though I'm quite liking **Vuze**. I'm always looking for apps to recommend to others, even if I don't even use them myself. I have always been pushing KTorrent as my bittorrent client of choice, but obviously it has let me down, and I might not necessarily promote Vuze to others, since to many it might be overcomplicated.

I noticed early on some of the other apps out there are too simplistic, so KTorrent was the perfect choice. I did have a look at **Transmission** before Vuze, and realised this one only appeared to be one of the simplistic ones (double-clicking a download shows a lot more info and options). But I did a test and **Transmission** and **KTorrent** were doing the same speed on the same torrents... maybe I could have picked ones with more seeds or something... but I decided to keep trying other apps, and now I have Vuze downloading much faster than both those apps... including ones that in KTorrent were still at 0.00% because it either couldn't find peers or just couldn't get anything from them. I am now happily downloading ones like this at a decent pace, while for days couldn't get a nibble in KTorrent.

So while on the one hand logic dictates that unless I've mucked with the settings (at least in a way detrimental to download speeds), all the programs for this task should be relatively the same, empirical evidence is showing me that something is amiss in KTorrent (and perhaps even Transmission). It wasn't always the case, but for a few weeks now I have watched as KTorrent struggles to get anything from peers (occassionally on certain torrents it would be quite fast, like nothing has gone awry, but that usually doesn't last too long).

I am hoping one of you braniacs can shed some light on this (just for peace of mind), as obviously Vuze is doing something very right, and KTorrent is doing something very wrong. It must have to do with ports or something (that I probably don't understand), but like I said, I haven't touched any of that, and have played around with things like seeding speeds etc to no avail (the settings I had since Oct 2006 always served me well till recently, but I have tried everything now that things have gone amiss).

Anyway, an immediate answer to anyone experiencing the same with KTorrent is try Vuze, and maybe Frostwire.

---

### Post by cb951303 on 2008-12-15
Have you configured your ports properly?
AS you know bittorrent needs a properly forwarded port for high speeds. There some protocols such as upnp to make it possible automatically but maybe there was a problem with ktorrent's upnp feature?

I always forward my ports manually from the routers config page.
Here is a good start: [http://portforward.com/](http://portforward.com/)

---

### Post by OzzyFrank on 2008-12-15
Hi. I've always just relied on default ports and they've always been OK (till recently, I suppose). Like I said, I haven't changed any of them, so unless an update to KTorrent did, they should be as before. Even though there has never been any need to configure ports manually, I'm always open to suggestions to make downloads faster, especially now. If the default ports in KTorrent are crappy ones, it would explain the difference between it and Vuze. But dunno why it all started going sour a few weeks back... from first glance, the ports seem to be the same. At least I am getting full speed in Vuze, but I do like KTorrent, so wouldn't mind seeing if I can fix it. I'll have a look at that ports page. Cheers.

---

### Post by cb951303 on 2008-12-15
> **OzzyFrank said:**
> Hi. I've always just relied on default ports and they've always been OK (till recently, I suppose). Like I said, I haven't changed any of them, so unless an update to KTorrent did, they should be as before. Even though there has never been any need to configure ports manually, I'm always open to suggestions to make downloads faster, especially now. If the default ports in KTorrent are crappy ones, it would explain the difference between it and Vuze. But dunno why it all started going sour a few weeks back... from first glance, the ports seem to be the same. At least I am getting full speed in Vuze, but I do like KTorrent, so wouldn't mind seeing if I can fix it. I'll have a look at that ports page. Cheers.

like I said it may be a bug or regression with the current ktorrent version. you can check bugzilla if you want. But a manual port forwarding would always work that's why I don't rely on automatic port configuration.

Just forward/open a port (I like using 11333 cause it was the default in azureus and I was used to it) from the link I sent and then enter the same port number to you ktorrent port settings. Restart the application, voila!

---

### Post by OzzyFrank on 2008-12-15
From the Azureus/Vuze FAQ regarding getting good download speeds:

**"... you don't use a standard incoming listen port like 6881"**

Guess what the default port in KTorrent is, hehe?

---

### Post by cb951303 on 2008-12-15
> **OzzyFrank said:**
> From the Azureus/Vuze FAQ regarding getting good download speeds:

**"... you don't use a standard incoming listen port like 6881"**

Guess what the default port in KTorrent is, hehe?

that may be the problem, however I would manually open a port and use it just to be sure

---

### Post by OzzyFrank on 2008-12-15
Also, I noticed in Plugins there is a UPnP one, but it isn't enabled. I might try that first, since Vuze has it enabled.

---

### Post by OzzyFrank on 2008-12-15
> **cb951303 said:**
> that may be the problem, however I would manually open a port and use it just to be sure

How do you do that? Do you just mean change the port # in Options, or test the port through some arcane means? I was just going to change the port, though might try the UPnP plugin and see if it makes any difference. (I'll do that a bit later as I'm nearing the end of a download KTorrent couldn't even start and I'd given up hope on... plenty of those still in KTorrent for me to test settings with!).

---

### Post by cb951303 on 2008-12-15
> **OzzyFrank said:**
> How do you do that? Do you just mean change the port # in Options, or test the port through some arcane means? I was just going to change the port, though might try the UPnP plugin and see if it makes any difference. (I'll do that a bit later as I'm nearing the end of a download KTorrent couldn't even start and I'd given up hope on... plenty of those still in KTorrent for me to test settings with!).

yes you need to change the port in ktorrent settings but first you need to forward/open that port from your router settings. Try the link from my first post to see how you open a port for your router.

---

### Post by OzzyFrank on 2008-12-15
Out of curiosity, would specifying a port that is already working (ie: the one Azureus uses) bypass the need for that? By the way, from that page I looked at suggested ports, and the one for Azureus was 6881, hehe.

---

### Post by cb951303 on 2008-12-15
> **OzzyFrank said:**
> Out of curiosity, would specifying a port that is already working (ie: the one Azureus uses) bypass the need for that? By the way, from that page I looked at suggested ports, and the one for Azureus was 6881, hehe.

upnp specifies a new port everytime you open azureus so there isn't actually "one" working port but there are many however when you exit the application, that ports return to their primal states which are "closed" meaning there are no "already working" ports on your computer.

Okay, I see you're getting confused so do this. Try enabling upnp plugin in ktorrent and see if it works if not than open up your router settings. Forward the port 11333 to your local ip from NAT settings (see the link for how). Restart your router. Open up ktorrent, input 11333 for port number.

6881 for azureus means absolutely nothing. you can specify any port you want as long as it's not already used by another application. 11333 is a safe bet.

---

