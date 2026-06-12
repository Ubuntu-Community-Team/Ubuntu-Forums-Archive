---
title: "my transmission bit torrent client dont download from all peers"
date: 2009-04-25
forum: General Help
---

### Post by mallan on 2009-04-25
I have a problem with slow downloads.. the transmission torrent client in ubuntu dont download from all the connected peers.. pls help

---

### Post by |Mitch| on 2009-04-25
Do you have the port forwarded in your router settings?

---

### Post by lovinglinux on 2009-04-26
> **mallan said:**
> the transmission torrent client in ubuntu dont download from all the connected peers..

That's absolutely normal. The peers from whom you download/upload keeps changing all the time. Peers can't upload to everyone they connect, otherwise each destination would receive only a small fraction of their bandwidth. But they keep the connection establish, so once they have the pieces you want and they have an uploading slot available they will upload to you.

You also can't upload to everyone, so you need to choose a number of uploading slots that will give at least a decent fraction of your bandwidth to each peer. Your client should have a preference setting to choose the number of uploading slots. I use Deluge, so I don't know if Transmisson has it or use a default value. 

For example, my upload limit is 50KiB/s and I have enable only 5 uploading slots, so if my client distributes the bandwidth evenly, then each peer will receive 10KiB/s from me. But if I enable 50 uploading slots, then each peer could receive only 1KiB/s. It doesn't work like this tho. Usually your client will give more bandwidth in the upload to those that give you more for you to download, but setting up too many upload slots is not recommended, since it might slow down your downloads, unless you are lucky enough to connect only to seeders.

So if everyone has a limited number of uploading slots but connect to hundreds of users, then everyone can't download all the time from everyone they connect .

You should indeed check if the port configured in the torrent client to receive connections is open in the router. This is not a big problem when you are able connect to several peers, because a closed port  just means you will not accept connections from remote peers requests. But once you are connected to a peer, the port being open or not in the router does not affect the speed of this connection. Nevertheless, you would like to optimize your chances of connecting to peers, specially if the torrent swarm has only a few of them. So an open port can help a lot to establish more connections and thus raising your chances of receiving more bandwidth in overall.

Bottom-line, you are probably downloading a bad torrent with too many leechers (downloaders) and a few seeders (uploaders) or your torrent is not configured properly to optimize the data transfer. Some things that might help:

[list][*] Check if you have too many overall connections enabled. I use 150
[*] Check if your upload speed is set to unlimited. It shouldn't be. Configure it to use only 80% of the upload limit imposed by your ISP. 
[*] Check if you have too many upload slots enabled
[*] Check if the number of half-open connections is too low or too high. I use 50.
[*] Check if the maximum connections attemp per second is not too high or too low. I use 20
[*] Check if you have too many active torrents. I usually allow only 2 active torrents at the same time[/list]

---

