---
title: "rtorrent not downloading"
date: 2009-02-19
forum: General Help
---

### Post by AbsentHarvest on 2009-02-19
Here is my ~/.rtorrent.rc

```
# This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.

# Maximum and minimum number of peers to connect to per torrent.
min_peers = 0
max_peers = 200

# Same as above but for seeding completed torrents (-1 = same as downloading)
min_peers_seed = 0
max_peers_seed = 200

# Maximum number of simultanious uploads per torrent.
max_uploads = 5

# Global upload and download rate in KiB. "0" for unlimited.
#download_rate = 0
#upload_rate = 0

# Default directory to save the downloaded torrents.
#directory = ./Torrents/Complete

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = ./Torrents/Downloading

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=./Torrents/TorrentFiles/auto/*.torrent
schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
#schedule = low_diskspace,5,60,close_low_diskspace=100M

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
schedule = ratio,60,60,"stop_on_ratio=200,200M,2000"

# The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no

# The ip address the listening socket and outgoing connections is
# bound to.
#bind = 127.0.0.1
#bind = rakshasa.no

# Port range to use for listening.
port_range = 6890-6890

# Start opening ports at a random position within the port range.
port_random = no

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
#check_hash = no

# Set whetever the client should try to connect to UDP trackers.
#use_udp_trackers = yes

# Alternative calls to bind and ip that should handle dynamic ip's.
#schedule = ip_tick,0,1800,ip=rakshasa
#schedule = bind_tick,0,1800,bind=rakshasa

# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
# encryption = allow_incoming,enable_retry,prefer_plaintext

# Enable DHT support for trackerless torrents or when all trackers are down.
# May be set to "disable" (completely disable DHT), "off" (do not start DHT),
# "auto" (start and stop DHT as needed), or "on" (start DHT immediately).
# The default is "off". For DHT to work, a session directory must be defined.
#
# dht = auto

# UDP port to use for DHT.
#
# dht_port = 6881

# Enable peer exchange (for torrents not marked private)
#
# peer_exchange = yes

#
# Do not modify the following parameters unless you know what you're doing.
#

# Hash read-ahead controls how many MB to request the kernel to read
# ahead. If the value is too low the disk may not be fully utilized,
# while if too high the kernel might not be able to keep the read
# pages in memory thus end up trashing.
#hash_read_ahead = 10

# Interval between attempts to check the hash, in milliseconds.
#hash_interval = 100

# Number of attempts to check the hash while using the mincore status,
# before forcing. Overworked systems might need lower values to get a
# decent hash checking rate.
#hash_max_tries = 10
```

Ports 6890-6890 (To IP Address: 192 . 168 . 0. 112) Enabled (Both UDP & TCP) I also set up the Torrents directory in Home along with Complete, Downloading and TorrentFiles - Auto.

Any suggestions?

---

### Post by AbsentHarvest on 2009-02-20
:popcorn:Bump.

---

### Post by AbsentHarvest on 2009-02-21
*Sigh* Doesn't anyone know how to fix this? :(

---

### Post by sandyd on 2009-02-21
have you set up something like ufw, firestarter, guarddog, or any firewall on your comp recently?

some tweaks to your config
```

# This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.

# Maximum and minimum number of peers to connect to per torrent.
min_peers = 0
max_peers = 200

# Same as above but for seeding completed torrents (-1 = same as downloading)
min_peers_seed = 0
max_peers_seed = 200

# Maximum number of simultanious uploads per torrent.
max_uploads = 5

# Global upload and download rate in KiB. "0" for unlimited.
#download_rate = 0
#upload_rate = 0

# Default directory to save the downloaded torrents.
#directory = ./Torrents/Complete

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = ./Torrents/Downloading

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=./Torrents/TorrentFiles/auto/*.torrent
schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
#schedule = low_diskspace,5,60,close_low_diskspace=100M

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
schedule = ratio,60,60,"stop_on_ratio=200,200M,2000"

# The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no

# The ip address the listening socket and outgoing connections is
# bound to.
bind = 192.168.0.112
#bind = rakshasa.no

# Port range to use for listening.
port_range = 6890-6890

# Start opening ports at a random position within the port range.
port_random = no

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
#check_hash = no

# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = yes

# Alternative calls to bind and ip that should handle dynamic ip's.
#schedule = ip_tick,0,1800,ip=rakshasa
#schedule = bind_tick,0,1800,bind=rakshasa

# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
 encryption = allow_incoming,enable_retry,prefer_plaintext

# Enable DHT support for trackerless torrents or when all trackers are down.
# May be set to "disable" (completely disable DHT), "off" (do not start DHT),
# "auto" (start and stop DHT as needed), or "on" (start DHT immediately).
# The default is "off". For DHT to work, a session directory must be defined.
#
 dht = auto

# UDP port to use for DHT.
#
 dht_port = 6881

# Enable peer exchange (for torrents not marked private)
#
 peer_exchange = yes

#
# Do not modify the following parameters unless you know what you're doing.
#

# Hash read-ahead controls how many MB to request the kernel to read
# ahead. If the value is too low the disk may not be fully utilized,
# while if too high the kernel might not be able to keep the read
# pages in memory thus end up trashing.
#hash_read_ahead = 10

# Interval between attempts to check the hash, in milliseconds.
#hash_interval = 100

# Number of attempts to check the hash while using the mincore status,
# before forcing. Overworked systems might need lower values to get a
# decent hash checking rate.
#hash_max_tries = 10
```

---

### Post by AbsentHarvest on 2009-02-22
No. I haven't set up any firewalls whatsoever on this computer.
I Entered in your version of the .rtorrent.rc and I got this...

```
zack@Ethergy:~$ gedit ~/.rtorrent.rc
zack@Ethergy:~$ rtorrent
rtorrent: Could not open/bind port for listening: Cannot assign requested address
zack@Ethergy:~$ 

```

---

### Post by AbsentHarvest on 2009-02-22
I mean, I never put a firewall up.. is there one by default?

---

### Post by _noob_ on 2009-02-22
Seems that you need to forward a port from your router to your computer. It may also help if you install a firewall. There is a default firewall but you have to configure it. I think at least. Sorry if this doesn't help a lot.

---

### Post by AbsentHarvest on 2009-02-22
well, I thought i forwarded the port. here i have a screenshot.
take a look.
[http://i544.photobucket.com/albums/hh324/NOD62/Screenshot-2.png](http://i544.photobucket.com/albums/hh324/NOD62/Screenshot-2.png)
atleast that's how i thought i'm suppose to do it.

and why would a firewall help the situation?

---

### Post by _noob_ on 2009-02-22
> **AbsentHarvest said:**
> well, I thought i forwarded the port. here i have a screenshot.
take a look.
[http://i544.photobucket.com/albums/hh324/NOD62/Screenshot-2.png](http://i544.photobucket.com/albums/hh324/NOD62/Screenshot-2.png)
atleast that's how i thought i'm suppose to do it.

and why would a firewall help the situation?

Oops. Lol. The firewall was for WoW. Sorry. But Test a port or two to make sure that they are open. If you will.

---

### Post by AbsentHarvest on 2009-02-22
how am I suppose to test it?

---

### Post by AbsentHarvest on 2009-02-22
would it help if i gave you a bit of information on my connection?

```
eth0      Link encap:Ethernet  HWaddr 00:21:9b:07:3b:41  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:9bff:fe07:3b41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35533 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:41187268 (41.1 MB)  TX bytes:4713893 (4.7 MB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by _noob_ on 2009-02-22
[http://www.canyouseeme.org/](http://www.canyouseeme.org/) . Try this. It may help

---

### Post by AbsentHarvest on 2009-02-22
```

Error: I could not see your service on 99.252.170.18 on port (6890)
Reason: No route to host
```

Uhm. How can I fix this? Lol.
I've tried doing single port forwarding and still isn't working.

---

### Post by _noob_ on 2009-02-22
Honestly I really don't know how to fix it and I am currently out of suggestions. Sorry that I couldn't be more help.

---

### Post by AbsentHarvest on 2009-02-22
```
Success: I can see your service on 99.252.170.18 on port (6890)
Your ISP is not blocking port 6890
```

After adjusting some settings. My ip the router gave me is 192.168.0.104
I also went into .rtorrent.rc and made the changes to match.

```
# This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.

# Maximum and minimum number of peers to connect to per torrent.
min_peers = 0
max_peers = 200

# Same as above but for seeding completed torrents (-1 = same as downloading)
min_peers_seed = 0
max_peers_seed = 200

# Maximum number of simultanious uploads per torrent.
max_uploads = 5

# Global upload and download rate in KiB. "0" for unlimited.
#download_rate = 0
#upload_rate = 0

# Default directory to save the downloaded torrents.
#directory = ./Torrents/Complete

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = ./Torrents/Downloading

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=./Torrents/TorrentFiles/auto/*.torrent
schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
#schedule = low_diskspace,5,60,close_low_diskspace=100M

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
schedule = ratio,60,60,"stop_on_ratio=200,200M,2000"

# The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no

# The ip address the listening socket and outgoing connections is
# bound to.
bind = 192.168.0.104
#bind = rakshasa.no

# Port range to use for listening.
port_range = 6890-6890

# Start opening ports at a random position within the port range.
port_random = no

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
#check_hash = no

# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = yes

# Alternative calls to bind and ip that should handle dynamic ip's.
#schedule = ip_tick,0,1800,ip=rakshasa
#schedule = bind_tick,0,1800,bind=rakshasa

# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
 encryption = allow_incoming,enable_retry,prefer_plaintext

# Enable DHT support for trackerless torrents or when all trackers are down.
# May be set to "disable" (completely disable DHT), "off" (do not start DHT),
# "auto" (start and stop DHT as needed), or "on" (start DHT immediately).
# The default is "off". For DHT to work, a session directory must be defined.
#
 dht = auto

# UDP port to use for DHT.
#
 dht_port = 6881

# Enable peer exchange (for torrents not marked private)
#
 peer_exchange = yes

#
# Do not modify the following parameters unless you know what you're doing.
#

# Hash read-ahead controls how many MB to request the kernel to read
# ahead. If the value is too low the disk may not be fully utilized,
# while if too high the kernel might not be able to keep the read
# pages in memory thus end up trashing.
#hash_read_ahead = 10

# Interval between attempts to check the hash, in milliseconds.
#hash_interval = 100

# Number of attempts to check the hash while using the mincore status,
# before forcing. Overworked systems might need lower values to get a
# decent hash checking rate.
#hash_max_tries = 10
```

I can start rtorrent again.. HOWEVER it's still not downloading.
However... I noticed that I'm getting a random port or atleast I think it's a random port... Look here.

```
*** rTorrent 0.8.2/0.12.2 - Ethergy:6538 ***
```
When the port that is open is 6890.... hmmmmmmmmmmmmmmmmmm

---

### Post by _noob_ on 2009-02-22
It could be the torrent file as well I suppose.... Are any other ports open?

---

### Post by AbsentHarvest on 2009-02-22
No other ports are open.
Also, this torrent in fact works. I downloaded it moments ago on my other computer in record speed.
I also raised the max seeds and peers to 2000 since the peers/seed on this torrent are well around 1000.

---

### Post by _noob_ on 2009-02-22
Hmm... Could it be because there aren't enough ports open?

---

### Post by AbsentHarvest on 2009-02-22
Hmm. That sounds unusual.  You would think by now we'd at least hear someone else's two cents worth.

Seriously, anyone else can chime in. :]

I'm at a standstill, I don't know what else to do at this point.  I think it's coming up with random ports.. As I showed earlier.. 
> *** rTorrent 0.8.2/0.12.2 - Ethergy:6538 ***
But I've already set random ports to "no".... So.... :(

---

### Post by AbsentHarvest on 2009-02-22
I had a better look at it, and I changed things up a bit.
```
# This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.

# Maximum and minimum number of peers to connect to per torrent.
min_peers = 40
max_peers = 130

# Same as above but for seeding completed torrents (-1 = same as downloading)
min_peers_seed = 10
max_peers_seed = 50

# Maximum number of simultanious uploads per torrent.
max_uploads = 5

# Global upload and download rate in KiB. "0" for unlimited.
download_rate = 0
upload_rate = 0

# Default directory to save the downloaded torrents.
directory = /home/zack/Torrents/downloads

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /home/zack/Torrents/sessions

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/home/zack/Torrents/torrentfiles/*.torrent
schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
#schedule = low_diskspace,5,60,close_low_diskspace=100M

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
schedule = ratio,60,60,"stop_on_ratio=200,200M,2000"

# The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no

# The ip address the listening socket and outgoing connections is
# bound to.
bind = 192.168.0.104
#bind = rakshasa.no

# Port range to use for listening.
port_range = 6890-6890

# Start opening ports at a random position within the port range.
# port_random = yes

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
#check_hash = no

# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = yes

# Alternative calls to bind and ip that should handle dynamic ip's.
#schedule = ip_tick,0,1800,ip=rakshasa
#schedule = bind_tick,0,1800,bind=rakshasa

# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
 encryption = allow_incoming,enable_retry,prefer_plaintext

# Enable DHT support for trackerless torrents or when all trackers are down.
# May be set to "disable" (completely disable DHT), "off" (do not start DHT),
# "auto" (start and stop DHT as needed), or "on" (start DHT immediately).
# The default is "off". For DHT to work, a session directory must be defined.
#
 dht = auto

# UDP port to use for DHT.
#
 dht_port = 6881

# Enable peer exchange (for torrents not marked private)
#
 peer_exchange = yes

#
# Do not modify the following parameters unless you know what you're doing.
#

# Hash read-ahead controls how many MB to request the kernel to read
# ahead. If the value is too low the disk may not be fully utilized,
# while if too high the kernel might not be able to keep the read
# pages in memory thus end up trashing.
#hash_read_ahead = 10

# Interval between attempts to check the hash, in milliseconds.
#hash_interval = 100

# Number of attempts to check the hash while using the mincore status,
# before forcing. Overworked systems might need lower values to get a
# decent hash checking rate.
#hash_max_tries = 10
```
It works now. ;)

---

