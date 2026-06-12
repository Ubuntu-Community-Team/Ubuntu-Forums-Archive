---
title: "Help with rTorrent"
date: 2006-10-06
forum: Desktop Environments
---

### Post by fernando_lopes_jr on 2006-10-06
I just installed rTorrent and setup up .rtorrent.vc but I’ am not sure if my configuration is the best to max out my connection could someone give me a hand with it until now I have this:

download_rate = 0
upload_rate = 30

port_range = 53000-53010
port_random = yes

min_peers = 50
max_peers = 150

max_uploads = 6

check_hash = yes

use_udp_trackers = yes

directory = ~/cda-server/Jr/Downloads

session = ~/cda-server/Jr/Downloads
schedule = watch_directory,10,10,load_start=~/cda-server/Jr/Downloads/*.torrent
schedule = tied_directory,10,10,start_tied=
schedule = untied_directory,10,10,close_untied=

I have an  8192/384 Kbps connection

---

### Post by konsole on 2006-10-08
> **fernando_lopes_jr said:**
> I just installed rTorrent and setup up .rtorrent.vc but I’ am not sure if my configuration is the best to max out my connection could someone give me a hand with it until now I have this:

port_range = 53000-53010
port_random = yes

min_peers = 50
max_peers = 150




I'll assume you made a typo and meant .rtorrent.rc :)

All looks ok but a couple of comments:

It's not necessary to forward more than 1 port, and the more you open the more you are visible. I would use: 
port_range = 53010-53010

150 max_peers per torrent is way overkill. 50 is plenty.

HTH

---

### Post by StarkD on 2007-01-08
I'm trying also looking for good settings for my rTorrent. I found a tutorial that seems to be useful: [http://torrentfreak.com/optimize-your-bittorrent-download-speed/]("http://torrentfreak.com/optimize-your-bittorrent-download-speed/") 

What are these about?
```
min_peers
max_peers
```

This is my .rtorrent.rc
```
# Maximum and minimum number of peers to connect to per torrent.
min_peers = 40
max_peers = 130

# Same as above but for seeding completed torrents (-1 = same as downloading)
min_peers_seed = 10
max_peers_seed = 50

# Maximum number of simultanious uploads per torrent.
max_uploads = 17

# Global upload and download rate in KiB. "0" for unlimited.
download_rate = 590
upload_rate = 100

# Default directory to save the downloaded torrents.
directory = /home/homedir/torrents/downloads

# Default session directory.
session = /home/homedir/torrents/sessions

# Watch a directory for new torrents, and stop those that have been deleted.
schedule = watch_directory,5,5,load_start=/home/homedir/torrents/torrentfiles/*.torrent
schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
schedule = low_diskspace,5,60,close_low_diskspace=100M

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
schedule = ratio,60,60,stop_on_ratio=200,200M,2000

# Port range to use for listening.
port_range = 7333-7333

# Start opening ports at a random position within the port range.
# port_random = yes

# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = yes
```

---

### Post by fernando_lopes_jr on 2007-02-01
I would also like to know how I can limit the number of torrentes downloaded to 3 torrents at a time

---

