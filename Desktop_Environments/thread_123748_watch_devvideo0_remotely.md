---
title: "watch /dev/video0 remotely?"
date: 2006-01-30
forum: Desktop Environments
---

### Post by veraction on 2006-01-30
So, I have a tv tuner card on my desktop that I can use with tvtime to watch tv (can't figure out mythtv yet).

Anyways, How would I go about watching it on my laptop? The connection is good enough. 500KB/s wireless or >10MB/s wired. I could host it on private web server, or any other method.

I tried vncviewer, but that didn't work. tried using x forwarding with ssh and that didn't either (the tvtime screen is just blank)

---

### Post by RAOF on 2006-01-30
[QUOTE=veraction]So, I have a tv tuner card on my desktop that I can use with tvtime to watch tv (can't figure out mythtv yet).

Anyways, How would I go about watching it on my laptop? The connection is good enough. 500KB/s wireless or >10MB/s wired. I could host it on private web server, or any other method.

I tried vncviewer, but that didn't work. tried using x forwarding with ssh and that didn't either (the tvtime screen is just blank)[/QUOTE]
You could probably use VLC - that has a streaming server & client.  I'm not sure of the details, but it shouldn't be too hard.

---

### Post by trancephorm on 2006-02-01
Recently, I managed to setup mpeg4ip.sf.net and Darwin streaming server together, for video streaming, but you can't put both programs on the same machine... Also, I think only mpeg4ip (actually mp4live program from that bundle) is sufficient for this task but I needed Darwin, so I didn't tried it alone...

---

### Post by lamadredelsapo on 2006-10-02
Actually i have mp4live and darwin streaming server working in the same machine and i have no problems at all. You should try with the latest version of mpeg4ip [http://mpeg4ip.sourceforge.net/downloads/index.php]("http://mpeg4ip.sourceforge.net/downloads/index.php") and Darwin streaming server 4.1.3.c

---

### Post by tagra123 on 2006-10-02
MythTv-suite should install from the repositories.  What problem are you having with it?

---

### Post by Rhubarb on 2006-10-02
VLC can unicast or multicast any (ok, most) video formats well.
Not too sure if it'll let you change channels though.
See [www.videolan.org](www.videolan.org) for details about getting streaming to work.
I've successfully got this running at home under windows, I think Ubuntu requires some extra dependencies to get the server part of it working.

---

### Post by patrick295767 on 2006-11-03
> **Rhubarb said:**
> VLC can unicast or multicast any (ok, most) video formats well.
Not too sure if it'll let you change channels though.
See [www.videolan.org](www.videolan.org) for details about getting streaming to work.
I've successfully got this running at home under windows, I think Ubuntu requires some extra dependencies to get the server part of it working.


> Stream tv to the network: 
   [B]vlc --color
   v4l:/dev/video2:norm=ntsc:frequency=77250:size=640x480:\
   adev=/dev/dsp2:audio=0 --sout #transcode{vcodec=mp4v,acodec=mpga,vb=512,\
   ab=128,samplerate=44100,venc=ffmpeg{keyint=80,hurry-up,vt=800000},\
   deinterlace}:std{access=mmsh,dst=:8080} --ttl 12 -I dummy [/B]

Receive: 
**   vlc mmsh://servername:8080**



Check this: [http://www.videolan.org/streaming-features.html](http://www.videolan.org/streaming-features.html)
dvb works
 
[http://www.linuxtv.org/v4lwiki/index.php/Streaming](http://www.linuxtv.org/v4lwiki/index.php/Streaming)
 
Concerning the vls; it was giving: 
```

# vls --help
VideoLAN Server 0.5.4+cvs20031028 (Oct 26 2005) - (c) 1999-2003 VideoLAN

 vls [options] target

 options:
   -v             --verbose      verbosity (v, vv, vvv)
   -h             --help         display this help
   -d <ip[:port]> --destination  ip and port destination
   -f <file>      --file <file>  configuration file
   -t <number>    --ttl <number> ttl value
   -l             --loop         looping at end of program
                  --log <file>   log to <file>

 target:
   dvd:<device>     for streaming of a dvd
   dvd:<dir>        for streaming of a dvd stored on hard drive
   file:<file>      for streaming of a file
   dvb:<channel>    for streaming of a dvb channel

```
only;

[I]So; while watching tv, you can record to file; 
if you wanna change channel; you can use : 
tvtime-command
via a script & passing by any open ports (nmap).[/I]:-) 
  
  
 ==
[http://www.gossamer-threads.com/lists/engine?do=post_view_printable;post=161275;list=mythtv](http://www.gossamer-threads.com/lists/engine?do=post_view_printable;post=161275;list=mythtv)
mplayer tv://14 -tv device=/dev/video0:driver=v4l2:width=512:height=384
Video: dd if=/dev/video0 of=test.mpg bs=64
[http://www.linuxtv.org/v4lwiki/index.php/TV_Viewing](http://www.linuxtv.org/v4lwiki/index.php/TV_Viewing)
XdTV -- XdTV is a software that allows you to watch record & stream TV
[http://www.linuxtv.org/v4lwiki/index.php/Streaming](http://www.linuxtv.org/v4lwiki/index.php/Streaming)
[http://blog.tmcnet.com/blog/tom-keating/voip/streaming-live-tv.asp](http://blog.tmcnet.com/blog/tom-keating/voip/streaming-live-tv.asp)
sopcast deb [http://ubuntuforums.org/showthread.php?t=258049](http://ubuntuforums.org/showthread.php?t=258049)

Greetz

---

### Post by patrick295767 on 2006-11-04
I just saw that with openmash we could remote the video
for video conferencing 

maybe it could work with /dev/video0

I never tried this yet

[http://www.linuxjournal.com/article/5614](http://www.linuxjournal.com/article/5614)
> This is where MASH comes into play. MASH is actually a collection of tools produced by the Open MASH Consortium (created by Larry Rowe and Steve McCanne). Their purpose was to create a public domain toolkit for developing collaboration and streaming applications. MASH stands for multimedia architecture that scales across heterogenous environments. No, really. It is all true.

If you feel so inclined, you can download the source and build the package from scratch:
tar -xzvf mash-src-5.1.5.tar.gz
cd mash-code
./build


The easiest method is to download the precompiled binary package from the Open MASH web site at [www.openmash.org](www.openmash.org). Once that is done, you merely extract the package and run the installation script. Observe, mes amis:
tar -xzvf mash-bin-5.1.5-linux-gnu.tar.gz
cd mash-5.1.5
./setup.sh

So simple, non? As I mentioned, this is a collection of tools rather than a single program. The most interesting one however, particularly for François, is vic, the video-conferencing tool that allows for multiple users to participate in video communication: 
vic hostname/port_no

For instance, if I wanted to connect to a machine called speedy on my network on port 2002, I would issue the command like this: 
vic speedy/2002

You should see a small window pop up at this point with a simple message, ``Waiting for video...'', in the center of it. The video you are waiting for, of course, is the young lady at table 22. For the young ladies out there, it may well be François. Who knows? While we wait for the other side of the connection, click the Menu button. A control window will appear that gives you control over many aspects of the current session. Look at the top of that window and click on the Transmit button. Even without the other side of the connection, you will see a small image of yourself sitting behind your camera. 


Now, click on the small image. A somewhat larger session image appears. When the person on the other end comes on-line, their image will appear, and you can follow the same procedure to detach a more appetizing view. Figure 3 shows François talking to the mysterious lady using vic. As you can see from the image, he even is afraid to let his own image be seen and has provided an avatar of sorts. Poor François.

---

### Post by patrick295767 on 2006-11-09
Vdr is nice program:

[http://www.vdr-wiki.de/wiki/index.php/Ubuntu_-_VDR_Streaming_Server_Installation](http://www.vdr-wiki.de/wiki/index.php/Ubuntu_-_VDR_Streaming_Server_Installation)


```

apt-get install vdr vdr-daemon vdr-dev vdradmin
cd /usr/src
apt-get build-dep vdr
apt-get source vdr
ln -s /var/lib/video.00 /video
chown vdr.vdr /video
#gedit  /etc/vdr/setup.conf &
cd /var/lib/vdr/
ln -s /etc/vdr/setup.conf setup.conf
ln -s /etc/vdr/channels.conf channels.conf
chown vdr.vdr *
/etc/init.d/vdr start
/etc/init.d/vdradmin start



```


and also very interstig about it: [http://mitglied.lycos.de/peterweber69/](http://mitglied.lycos.de/peterweber69/)

---

### Post by patrick295767 on 2006-11-09
[http://ivtvdriver.org/index.php/Howto:Netcat_streaming](http://ivtvdriver.org/index.php/Howto:Netcat_streaming)

---

