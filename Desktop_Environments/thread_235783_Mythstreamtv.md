---
title: "Mythstreamtv"
date: 2006-08-13
forum: Desktop Environments
---

### Post by xinix on 2006-08-13
Does anyone have mythstreamtv working properly with Ubuntu?  I can get it stream video but I get errors for sound. I'm using mythstreamtv 0.98 available from: [http://jogibear9988.dyndns.org:2080/]("http://jogibear9988.dyndns.org:2080/") 
I have installed  ffmpeg from the main repository and vlc from this repo:
```
deb http://nightlies.videolan.org/build/dapper-i386 /
```
The error:
```
Starting Stream of /Mythtv/Recordings/1059_20060813030000.mpg
VLC media player 0.8.5 Janus
[00000274] main interface: creating httpd
[00000293] ffmpeg encoder error: cannot find encoder MPEG Audio layer 1/2/3
[00000280] stream_out_transcode private error: cannot find encoder
[00000280] stream_out_transcode private error: cannot create audio chain
[00000291] main packetizer error: cannot create packetizer output (mpga)
```

I have also tried building vlc from source with no success.  Even using the ubuntu source package compiling fails.  Ffmpeg builds fine and I have tried various sources (svn, ubuntu source package, released stable source code) but I'm pretty sure the problem lies in vlc.

---

