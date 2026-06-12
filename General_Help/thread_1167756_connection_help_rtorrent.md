---
title: "connection help rtorrent"
date: 2009-05-23
forum: General Help
---

### Post by Neural oD on 2009-05-23
Hi All

What I have is this scenario. I am the administrator of a lan. I am having difficulty allowing rtorrent to connect. The setup is as such: proxy/firewall on 10.0.1.5, client 10.0.1.3 wants to connect via rtorrent. On 10.0.1.5 I have the relevant iptables on a script as such: IPT="/usr/sbin/iptables" and EIF="eth0". > #$IPT -I FORWARD -i $EIF -s 10.0.1.3 -j ACCEPT
$IPT -I FORWARD -i $EIF -d 10.0.1.3 -p tcp --dport 51312 -j ACCEPT
$IPT -A FORWARD -i $EIF -m state --state ESTABLISHED,RELATED -d 10.0.1.3 -j ACCEPT
$IPT -t nat -A PREROUTING -p tcp -d 0.0.0.0/0 --dport 51312 -s 0.0.0.0/0 -j DNAT --to-destination 10.0.1.3:51312
$IPT -t nat -I POSTROUTING -s 10.0.1.3 -p tcp -m tcp --sport 51312 -o $EIF -j SNAT --to-source 196.33.247.2

$IPT -I FORWARD -i $EIF -d 10.0.1.3 -p udp --dport 6881 -j ACCEPT
$IPT -t nat -A PREROUTING -p udp -d 0.0.0.0/0 --dport 6881 -s 0.0.0.0/0 -j DNAT --to-destination 10.0.1.3:6881
$IPT -t nat -I POSTROUTING -s 10.0.1.3 -p udp -m udp --sport 6881 -o $EIF -j SNAT --to-source 196.33.247.2

Obviously rtorrent listens on the client machine on 51312 and listens on port 6881 for udp - DHT.

The proxy which is running squid allows unrestricted access to 10.0.1.3.

The problem is this - when running rtorrent - I can see the trackers, but the peers are not comming up - which i think is due maybe to the udp?? 
Here is my .rtorrentrc file: ```
# This is an example resource file for rTorrent. Copy to 
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.
 
# Maximum and minimum number of peers to connect to per torrent.
#min_peers = 40
#max_peers = 100
 
# Same as above but for seeding completed torrents (-1 = same as downloading)
#min_peers_seed = 10
#max_peers_seed = 50
 
# Maximum number of simultanious uploads per torrent.
#max_uploads = 15
 
# Global upload and download rate in KiB. "0" for unlimited.
#download_rate = 0
upload_rate = 7
 
# Default directory to save the downloaded torrents.
directory = /home/anthony/downloads/torrents/
 
# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
#session = ./session
 
# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start="/home/anthony/downloads/torrents/.watch/*.torrent"
#schedule = untied_directory,5,5,stop_untied=
 
# Close torrents when diskspace is low.
#schedule = low_diskspace,5,60,close_low_diskspace=100M
 
# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
#schedule = ratio,60,60,"stop_on_ratio=200,200M,2000"
 
# The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no
#ip = 196.33.247.2
 
# The ip address the listening socket and outgoing connections is
# bound to.
#bind = 127.0.0.1
#bind = rakshasa.no
 
# Port range to use for listening.
#port_range = 6890-6999
port_range = 51312-51312
 
# Start opening ports at a random position within the port range.
#port_random = yes

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
 encryption = allow_incoming,try_outgoing,enable_retry

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

http_proxy=http://10.0.1.5:8080


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

```

Any help would be really appreciated!

---

### Post by mellowd on 2009-05-23
Just out of interest, why do you want to have bitorrent running through a proxy?

---

### Post by Neural oD on 2009-05-23
> **mellowd said:**
> Just out of interest, why do you want to have bitorrent running through a proxy?
thx for the quick reply!
well I'm not really wanting to have bittorrent running on the proxy/firewall machine. Therefore it needs to access the outside world via the proxy. Is this a problem with rtorrent??

---

### Post by mellowd on 2009-05-23
I doubt it's a problem with rtorrent, although my set up is slightly different. 

I assume you have something like this:

[router]---[server/proxy]---[client]


is this right?

---

### Post by Neural oD on 2009-05-23
> **mellowd said:**
> I doubt it's a problem with rtorrent, although my set up is slightly different. 

I assume you have something like this:

[router]---[server/proxy]---[client]


is this right?
THat's exactly the setup

---

### Post by Neural oD on 2009-05-23
@mellowd
[router]---[server/proxy]---[client]

Is this your setup - and is it working??

---

### Post by mellowd on 2009-05-23
If you disable DHT and UDP, are you able to connect with no problems via TCP?

---

### Post by mellowd on 2009-05-23
> **Neural oD said:**
> @mellowd
[router]---[server/proxy]---[client]

Is this your setup - and is it working??


No mine is different 

[cable modem] - [wireless router] - [clients/server]

i.e. my pc and server are both connected straight to the router via cable and my netbook wireless. I don't use the server itself as any sort of proxy or router

---

### Post by Neural oD on 2009-05-23
> **mellowd said:**
> If you disable DHT and UDP, are you able to connect with no problems via TCP?
great - let me give that a go - I assume it's only the settings in the rtorrentrc file that needs changing?

---

### Post by Neural oD on 2009-05-23
@mellowd

Thx for the great help so far - but unfortunately I'm still not able to connect to the peers? Any other suggestions?

---

### Post by mellowd on 2009-05-23
Hmm, I'll be honest and tell you know that my iptables knowledge is limited. At work I'm so used to hardware firewalls that all I even configure iptables for generally is to block unwanted traffic. 


I'm on shift now and quite busy, I'll have a crack at it again tomorrow. In the meantime if anyone else has any ideas so far...

---

### Post by Neural oD on 2009-05-23
> **mellowd said:**
> Hmm, I'll be honest and tell you know that my iptables knowledge is limited. At work I'm so used to hardware firewalls that all I even configure iptables for generally is to block unwanted traffic. 


I'm on shift now and quite busy, I'll have a crack at it again tomorrow. In the meantime if anyone else has any ideas so far...

NP - thx for the help thus far - I'll keep checking in periodically :)

---

### Post by Neural oD on 2009-05-23
BUMP

Anyone??

---

### Post by Neural oD on 2009-05-24
Bump

My feeling in this is that I'm not getting two way communication with udp?! Not sure if this is correct - any thoughts out there on udp through a proxy(squid)?

---

### Post by Neural oD on 2009-05-26
BUMP

No ideas on this guys?? 
I know there should be some networking genius's out there??

---

### Post by dwouters on 2009-05-26
> **Neural oD said:**
> Hi All

What I have is this scenario. I am the administrator of a lan. I am having difficulty allowing rtorrent to connect. The setup is as such: proxy/firewall on 10.0.1.5, client 10.0.1.3 wants to connect via rtorrent. On 10.0.1.5 I have the relevant iptables on a script as such: IPT="/usr/sbin/iptables" and EIF="eth0". 
Obviously rtorrent listens on the client machine on 51312 and listens on port 6881 for udp - DHT.

The proxy which is running squid allows unrestricted access to 10.0.1.3.

The problem is this - when running rtorrent - I can see the trackers, but the peers are not comming up - which i think is due maybe to the udp?? 
Here is my .rtorrentrc file: ```
# This is an example resource file for rTorrent. Copy to 
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.
 
# Maximum and minimum number of peers to connect to per torrent.
#min_peers = 40
#max_peers = 100
 
# Same as above but for seeding completed torrents (-1 = same as downloading)
#min_peers_seed = 10
#max_peers_seed = 50
 
# Maximum number of simultanious uploads per torrent.
#max_uploads = 15
 
# Global upload and download rate in KiB. "0" for unlimited.
#download_rate = 0
upload_rate = 7
 
# Default directory to save the downloaded torrents.
directory = /home/anthony/downloads/torrents/
 
# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
#session = ./session
 
# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start="/home/anthony/downloads/torrents/.watch/*.torrent"
#schedule = untied_directory,5,5,stop_untied=
 
# Close torrents when diskspace is low.
#schedule = low_diskspace,5,60,close_low_diskspace=100M
 
# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
#schedule = ratio,60,60,"stop_on_ratio=200,200M,2000"
 
# The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no
#ip = 196.33.247.2
 
# The ip address the listening socket and outgoing connections is
# bound to.
#bind = 127.0.0.1
#bind = rakshasa.no
 
# Port range to use for listening.
#port_range = 6890-6999
port_range = 51312-51312
 
# Start opening ports at a random position within the port range.
#port_random = yes

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
 encryption = allow_incoming,try_outgoing,enable_retry

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

http_proxy=http://10.0.1.5:8080


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

```

Any help would be really appreciated!

Hey boss. Your proxy will need to be setup to allow incoming and outgoing connections for the IP address of your computer, which I assume is 10.0.1.3. You may also need to adjust your setting in squid and allow the same to IP 10.0.1.5. That should do the trick.

---

### Post by Neural oD on 2009-05-26
> **dwouters said:**
> Hey boss. Your proxy will need to be setup to allow incoming and outgoing connections for the IP address of your computer, which I assume is 10.0.1.3. You may also need to adjust your setting in squid and allow the same to IP 10.0.1.5. That should do the trick.
Thanks dwouters - at the moment - all traffic is allowed for that address - through the squid proxy. What I'm thinking is that squid is an http proxy - and I personally think that the issue I'm having is with the bittorrent seeders - which I think uses udp protocol. Not too sure about what to do - but need to look at setting up a socks proxy or something - would need some clarification on this though! It's really strange that no one else has seemed to write about this situation? Anyway I shall forge ahead - will post any developments - if any!?!

---

