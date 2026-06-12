---
title: "Question of the minds"
date: 2009-02-19
forum: General Help
---

### Post by faawhiz on 2009-02-19
I am new to the forums and am somewhat still new to ubuntu and linux in general. I have a question about a simple basic setup opinons are welcome.

** Current Setup
Ubuntu Laptop (nc6000) and (350mhz)Ubuntu Server 

My idea was to throw my mp3's & video's on the server box and play from there. Keep in mind, i remote to the server via ssh. Also my server has a sound card (Turtle Beach Santa Cruz) and a set of nice speakers hooked up to it. That was my original idea. 


Me being new to linux and all was wondering if this was overall an ok deal or would be better off with some other OS on the server? Before i actually had windows XP and i was using Terminal Services Client but it took forever to do anything on it because of the speed or lack there of.

Thanks for listening.

---

### Post by sr20ve on 2009-02-19
You can setup an NFS share on your server to share out your MP3 and video files.

You can then setup a mount point and an fstab entry on your laptop to automount the share on boot.

That's the setup I have at home and have no issues streaming video from the wireless connection on my laptop.

---

### Post by faawhiz on 2009-02-19
but the problem is i don't really want to stream i want to use my soundcard/speakers from the (350mhz) server.

---

### Post by faawhiz on 2009-02-19
anyone else have any idea's?

---

### Post by heindsight on 2009-02-19
One option is to install mpd on the server. mpd (Music Player Daemon) is a server program that plays music, the basic idea is that you have a library of music on your server and you can control playback over the network by connecting to the server using an mpd client. Have a look at [http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki](http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki) for more info on mpd.

There are several mpd clients available that you can install on your client machines, including a firefox plugin called Minion (which is what I usually use). [http://mpd.wikia.com/wiki/Clients#Ready_for_General_Use](http://mpd.wikia.com/wiki/Clients#Ready_for_General_Use) has a long list of clients you can use (Not all of them are available in the ubuntu repositories, I'd recommend either using Minion in firefox or one of the clients available in the repositories - I've also used Ario and found it works quite well).

---

