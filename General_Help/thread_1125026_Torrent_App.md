---
title: "Torrent App"
date: 2009-04-14
forum: General Help
---

### Post by hardon on 2009-04-14
I have a headless Ubuntu server with 3 Windows machines connected, as well as a modded Xbox. Basically its just a file/print server. 

I do a lot of downloading via torrents, and want to utilize the always-on aspect of the server. When the server was running XP, I achieved this by using Azureus (now Vuze)on the server, with the Azsmrc plugin on the client machines. That way I could d/l the torrents on whatever machine and have it start instantly on Azureus. Im wanting to do that again but I dont want to use Azureus (built on java = too much bloat). I was wondering what would be the best program to use to achieve this. The only two requirements I really have are: 

1. Able to control remotely (at the least be able to add d/l's remotely)

2. Able to load IP filters.

---

### Post by cariboo on 2009-04-14
I would suggest you have a look a rTorrent, it is in the repositories, you can install it on your server from the command line by typing:

```
sudo apt-get install rtorrent
```

There is also a web based front end called ftpg-www.

Jim

---

### Post by mb_webguy on 2009-04-14
Several torrent clients have a console interface, including rTorrent, Deluge, and Transmission.

rTorrent is a fairly popular text-only client.  I personally don't think the interface is very intuitive.  The first time I used it, I couldn't figure out how to quit, pull up the help information to find out how to quit, or really to do anything at all, and had to look up on the web how to control the darn thing.  The interface reminded me a bit of vi, actually.  But a lot of people seem to like it.

Transmission's CLI interface is pretty sparse, much like the GUI interface.  It's not so much an interface as a command to start torrent downloads or view downloads in progress.  It does the job, but I prefer something a bit more substantial.

I suppose I'm a bit partial to Deluge since I use the normal GUI client, but I was fairly impressed with the CLI client.  It feels a bit like a shell, with a prompt that takes various commands.  The commands themselves are fairly straightforward -- "help" shows the help file, "add" adds a torrent, "del" or "rm" remove a torrent, etc.  Just remember that you have to start the Deluge daemon (deluged) before you can use the client.

Deluge and a client called TorrentFlux have Web-based interfaces, which is another option for headless servers.

---

