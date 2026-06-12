---
title: "using an ubuntu server to create a media player with a web interface"
date: 2009-02-17
forum: General Help
---

### Post by buspital on 2009-02-17
I've been using Apple's remote app on my iphone to control an itunes library on a windows PC. The app is excellent, i just have to turn the PC on and I can play my music without having to turn on a monitor or anything. Unfortunately I dislike iTunes and it is lacking certain functionality that I'd like, such as the ability to create playlists. What I'd like to do is set up is an ubuntu machine which would have a web interface which could control a media player on the machine and to which I could add functionality as I require, but I've no idea how feasible this is.

Does anyone know if there is already an application that would allow me to do this, or if it is something I'll be able to set up myself? I'm not too sure where to start.

Ta

---

### Post by buspital on 2009-02-17
Anyone have any thoughts on this? Am I posting in the wrong place?

---

### Post by handy on 2009-02-17
Are you aware of [*_FreeNAS_*]("http://www.freenas.org/")?

It is a brilliant NAS server built on FreeBSD, it is tiny & very easy to install.  Once installed you use a client on your LAN to control & configure it via a web browser based GUI.

A FreeNAS box usually runs headless.

An installable & LiveCD multimedia distro called [*_GeeXboX_*]("http://www.geexbox.org/en/index.html") apparently interfaces very well with FreeNAS.

A problem that some people may have with FreeNAS, is that it is dedicated to this job.  You can not decide that you also want it to be your website server, or a firewall or anything else than what it was designed to do.

I use it to store important backup data & to store & stream video's over my home LAN.  For my purposes it is faultless. :-)

I'm using a PIII, to do the job, & a PII would be fine, for a home LAN, as the network speed is your bottleneck.

---

### Post by Sarastro on 2009-02-17
I like Handy's solution and there are several other ways to do this.

Building a simple, headless server offers the best flexibility of a central location for your music database (or anything else). These can be assembled from old hardware parts or purchased new.  They can be setup with a single hard drive or configured in a RAID setup.  It depends only upon your budget and individual storage requirements.

Interestingly as an option, Dell sells used machines with no OS for under $200. These can be a good start and inexpensively customized:

[http://www.dfsdirectsales.com/](http://www.dfsdirectsales.com/)

Here is a great tutorial which outlines one way to answer your media server questions:

[http://rubbervir.us/projects/ubuntu_media_server/](http://rubbervir.us/projects/ubuntu_media_server/)

Overall there are several ways to deliver music from your server to playback software elsewhere on your network:

1.  Mapping the server's music directory into your playback software.  For instance simply changing the default music directory in Rhythmbox (or whatever program you are using) to the server.

2.  [Mt-daapd]("http://wiki.mt-daapd.org/wiki/Quickstart_Ubuntu").  I believe this is what iTunes uses and setting up a daapd daemon on the server takes minutes.  Rhythmbox has built-in daapd functionality, there are plug-ins for other playback options such as Songbird.

3.  [MPD]("http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki").  Again, setting up the MPD daemon takes minutes and this is a very popular option.


Thirdly, remote control.  The above tutorial uses [Jinzora]("http://en.jinzora.com/features/jukebox_mode") but other options include:

1.  [SSH to control a daapd server]("http://wiki.fireflymediaserver.org/SSH_Tunnel")

2.  [XBMC]("http://xbmc.org/")

What I present here is simply an overview to several possible solutions to the media server/playback/control question.  I believe the idea of an individual's having a centralized music source is one which appeals to more and more listeners.

---

### Post by buspital on 2009-02-17
Thanks very much for the responses, but I don't think I was clear enough about what I am trying to do. 

I currently have a windows server box hosting my files and a windows desktop PC which runs itunes and has drives mapped to the server. Currently the desktop is set to log in automatically and fire up itunes automatically, thus getting it into the state i need without needing a monitor. This PC is connected to an amplifier and the remote app on the iphone allows me to view and control the itunes library on the PC (as the phone is connected wirelessly to the same network), thus enabling me to play the songs through the amplifier as selected on my iphone.
What I am trying to achieve is this same functionality, but removing itunes from the equation. I'd like to get some way of remote controlling the PC using my phone, I thought that this might be doable through some kind of web based application, so I can use the browser on my phone.

It maybe that this is stupid idea, I can accept that, but it would be great if I could knock at least one of the windows machines off my network. FreeNAS would be great for my server were it not for the fact that I run downloads on it. I'll probably put something else on it at some point, but it has no optical drives or graphics card which makes it a bit of a pain (it came with Windows home server preloaded)

---

### Post by mikewu on 2009-02-17
mpd does support a web interface for control. In fact it has a client optimized for the iPhone/iTouch

Clients:
[http://mpd.wikia.com/wiki/Clients](http://mpd.wikia.com/wiki/Clients)

Web Interface for iPhone:
[http://mpd.wikia.com/wiki/Client:IPodMp](http://mpd.wikia.com/wiki/Client:IPodMp)

---

### Post by buspital on 2009-02-17
Ah indeed, I think I rather misunderstood what it could do at first reading. Thanks very much everyone

---

### Post by handy on 2009-02-17
> **buspital said:**
> 
It maybe that this is stupid idea, I can accept that, but it would be great if I could knock at least one of the windows machines off my network. FreeNAS would be great for my server were it not for the fact that I run downloads on it. I'll probably put something else on it at some point, but it has no optical drives or graphics card which makes it a bit of a pain (it came with Windows home server preloaded)

FreeNAS does have Transmission as a built in service.  So if your downloads are torrents FreeNAS is happy to accept them, even to the point that it can be set up as a torrent slave with a watch directory.

Beyond that I'm sorry I can't help.

---

### Post by Sarastro on 2009-02-18
If I understand the OP's question correctly, you have a Window's server, a Window's desktop, and you're running Apple software which all involvles an Apple iPhone.

Whouldn't it be more appropiate to post this question in a Window's forum or maybe an Apple forum somewhere?

---

### Post by chayzer on 2009-02-20
I think what he's saying is that he wants to get away from the windows/itunes setup to play on his amp. Can't blame him.

My current setup is a cheap headless computer running ubuntu with mpd connected to an amp. I use a Nokia N800 running Maemo Music Player Client (just an mpd client). 

It's a great setup. I'm pretty sure there's a few iphone MPD clients out there.. I seem to recall coming across a couple when searching for clients.

---

