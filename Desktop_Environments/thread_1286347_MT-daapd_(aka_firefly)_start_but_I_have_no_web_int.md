---
title: "MT-daapd (aka firefly) start but I have no web interface"
date: 2009-10-08
forum: Desktop Environments
---

### Post by alek66 on 2009-10-08
I installed it with apt-get

when i do a sudo mt-daapd -f i get this
```
alek@darkstar:~$ sudo mt-daapd -f
Firefly Version svn-1696: Starting with debuglevel 2
Error loading plugin /usr/lib/mt-daapd/plugins/ssc-ffmpeg.so: /usr/lib/mt-daapd/plugins/ssc-ffmpeg.so: undefined symbol: avcodec_decode_audio
Error loading plugin /usr/lib/mt-daapd/plugins/ssc-script.so: plugin declined to load
Plugin loaded: daap/svn-1696
Plugin loaded: rsp/svn-1696
Starting signal handler
Starting rendezvous daemon
Client running
Initializing database
Full reload...
Starting mp3 scan
opendir: No such file or directory
Starting playlist scan
Updating playlists
Error scanning MP3 files: No such file or directory
Scanned 0 songs in 0 seconds
Starting web server from /usr/share/mt-daapd/admin-root on port 3689
Registering rendezvous names
Could not add mdns services: An unexpected D-Bus error occured
Could not add mdns services: Bad state
Could not add mdns services: Bad state
Serving 0 songs.  Startup complete in 0 seconds
Client failure
Server disconnected, reconnecting
Client running
Could not add mdns services: Daemon connection failed
Client failure
Server disconnected, reconnecting
Client running
Could not add mdns services: Daemon connection failed
Client failure
Server disconnected, reconnecting
Client running
Segmentation fault
```

What is causing this, and how can I fix it?

---

### Post by benoitg on 2009-10-22
See [https://bugs.launchpad.net/ubuntu/+source/mt-daapd/+bug/343069](https://bugs.launchpad.net/ubuntu/+source/mt-daapd/+bug/343069)

---

