---
title: "Beep Media Player and mp3 skip/bleeps/static"
date: 2006-01-01
forum: Desktop Environments
---

### Post by endangst on 2006-01-01
Hi! I just installed Ubuntu 5.10 and have been reading up on it for a few days to get acquainted with it.

I use Beep Media Player with libmpg123.so MPEG Audio Plugin.

However, mp3 playback (which play perfectly fine with Winamp in Windows XP), sometimes experiences "bleeps" and static/scratchy sounds at times, but most of the song sounds ok.  :confused: 

Is this due to a faulty or outdated mpeg codec?  Is there a newer or better mpeg codec available?

Thank you so much in advance for your help!

Sincerely,
Endang
 
Jakarta, Indonesia

---

### Post by audax321 on 2006-01-01
When I installed codecs, I just enabled the universe repository and did:

sudo apt-get install gstreamer0.8-plugins

OR, for just the gstreamer MP3 codec:

sudo apt-get install gstreamer0.8-mad

---

### Post by endangst on 2006-01-01
Hi, thanks for the reply.  I appreciate it.  

I installed the MP3 codec like you said, but Beep Media Player is still using the old codec.  Is there a way to update that?


endangst@ubuntu:~$ sudo apt-get install gstreamer0.8-mad
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libid3tag0 libmad0
The following NEW packages will be installed:
  gstreamer0.8-mad libid3tag0 libmad0
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 167kB of archives.
After unpacking 442kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main libid3tag0 0.15.1b-7 [34.9kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main libmad0 0.15.1b-2.1 [76.9kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe gstreamer0.8-mad 0.8.11-0ubuntu5 [55.5kB]
Fetched 167kB in 1m18s (2137B/s)

Preconfiguring packages ...
Selecting previously deselected package libid3tag0.
(Reading database ... 60221 files and directories currently installed.)
Unpacking libid3tag0 (from .../libid3tag0_0.15.1b-7_i386.deb) ...
Selecting previously deselected package libmad0.
Unpacking libmad0 (from .../libmad0_0.15.1b-2.1_i386.deb) ...
Selecting previously deselected package gstreamer0.8-mad.
Unpacking gstreamer0.8-mad (from .../gstreamer0.8-mad_0.8.11-0ubuntu5_i386.deb) ...
Setting up libid3tag0 (0.15.1b-7) ...

Setting up libmad0 (0.15.1b-2.1) ...

Setting up gstreamer0.8-mad (0.8.11-0ubuntu5) ...

endangst@ubuntu:~$

---

### Post by mcduck on 2006-01-01
have you done 'gst-register-0.8' already? run that in terminal and try BMP again..

---

### Post by endangst on 2006-01-01
mcduck
"have you done 'gst-register-0.8' already? run that in terminal and try BMP again.."

Hi there.  How do I do that?  Is that something I need to get from synaptic or the repository?  Sorry for the dumb question. hehheh.  I am a complete newbie.

---

### Post by endangst on 2006-01-01
Ok, it seems to have worked, but BMP still shows the old codec.

endangst@ubuntu:/$ gst-register-0.8
Trying to load global_registry ...
Added plugin xwindowlistener with 0 features.
Added plugin jpeg with 5 features.
Added plugin hermescolorspace with 1 feature.
Added plugin gsm with 2 features.
Added plugin gnomevfs with 2 features.
Added plugin dvdreadsrc with 1 feature.
Added plugin dvdnavsrc with 1 feature.
Added plugin gst1394 with 1 feature.
Added plugin cdparanoia with 1 feature.
Added plugin y4menc with 1 feature.
Added plugin wavenc with 1 feature.
Added plugin volume with 1 feature.
Added plugin volenv with 1 feature.
Added plugin videotestsrc with 1 feature.
Added plugin videoscale with 1 feature.
Added plugin videorate with 1 feature.
Added plugin videomixer with 1 feature.
Added plugin gstvideofilter with 0 features.
Added plugin videodrop with 1 feature.
Added plugin videocrop with 1 feature.
Added plugin videobox with 1 feature.
Added plugin videobalance with 1 feature.
Added plugin vcdsrc with 1 feature.
Added plugin vbidec with 1 feature.
Added plugin video4linux-radio with 1 feature.
Added plugin video4linux2 with 2 features.
Added plugin video4linux with 5 features.
Added plugin udp with 2 features.
Added plugin typefindfunctions with 70 features.
Added plugin tta with 2 features.
Added plugin timeoverlay with 1 feature.
Added plugin textoverlay with 2 features.
Added plugin gsttags with 1 feature.
Added plugin switch with 1 feature.
Added plugin subparse with 2 features.
Added plugin stereo with 1 feature.
Added plugin speed with 1 feature.
Added plugin spectrum with 1 feature.
Added plugin snapshot with 1 feature.
Added plugin smpte with 1 feature.
Added plugin smooth with 1 feature.
Added plugin sine with 1 feature.
Added plugin silence with 1 feature.
Added plugin shout2send with 1 feature.
Added plugin rtjpeg with 2 features.
Added plugin rtp with 4 features.
Added plugin rfbsrc with 1 feature.
Added plugin games with 1 feature.
Added plugin png with 2 features.
Added plugin playondemand with 1 feature.
Added plugin playbin with 1 feature.
Added plugin passthrough with 1 feature.
Added plugin overlay with 1 feature.
Added plugin navigationtest with 1 feature.
Added plugin nassink with 1 feature.
Added plugin multipart with 2 features.
Added plugin gstmultifilesink with 1 feature.
Added plugin mulaw with 2 features.
Added plugin mpegaudioparse with 1 feature.
Added plugin mpegaudio with 1 feature.
Added plugin mpeg2sub with 1 feature.
Added plugin mpeg1videoparse with 1 feature.
Added plugin monoscope with 1 feature.
Added plugin median with 1 feature.
Added plugin level with 1 feature.
Added plugin ladspa with 0 features.
Added plugin imagemixer with 1 feature.
Added plugin interleave with 2 features.
Added plugin gconfelements with 2 features.
Added plugin gamma with 1 feature.
Added plugin freeze with 1 feature.
Added plugin filter with 3 features.
Added plugin ffmpegcolorspace with 1 feature.
Added plugin effectv with 8 features.
Added plugin efence with 1 feature.
Added plugin dvdsubdec with 1 feature.
Added plugin dvdlpcmdec with 1 feature.
Added plugin deinterlace with 1 feature.
Added plugin decodebin with 1 feature.
Added plugin debug with 5 features.
Added plugin colorspace with 1 feature.
Added plugin chart with 1 feature.
Added plugin cairo with 2 features.
Added plugin cdplayer with 1 feature.
Added plugin auparse with 1 feature.
Added plugin audiorate with 1 feature.
Added plugin gstaudiofilter with 0 features.
Added plugin alphacolor with 1 feature.
Added plugin alpha with 1 feature.
Added plugin alaw with 2 features.
Added plugin ac3parse with 1 feature.
Added plugin gstvideo with 0 features.
Added plugin gstresample with 0 features.
Added plugin gstidct with 0 features.
Added plugin gstaudio with 0 features.
Added plugin gstspider with 2 features.
Added plugin gstindexers with 2 features.
Added plugin gstgetbits with 0 features.
Added plugin gstelements with 15 features.
Added plugin gstdataprotocol with 0 features.
Added plugin gstbytestream with 0 features.
Added plugin gstoptscheduler with 1 feature.
Added plugin gstoptomegascheduler with 1 feature.
Added plugin gstoptgthreadscheduler with 1 feature.
Added plugin gstfairgthreadscheduler with 1 feature.
Added plugin gstentryomegascheduler with 1 feature.
Added plugin gstentrygthreadscheduler with 1 feature.
Added plugin gstbasicomegascheduler with 1 feature.
Added plugin gstbasicgthreadscheduler with 1 feature.
Added plugin mad with 5 features.
Added plugin xvimagesink with 1 feature.
Added plugin ximagesink with 2 features.
Added plugin vorbis with 4 features.
Added plugin theora with 2 features.
Added plugin speex with 2 features.
Added plugin sdlvideosink with 1 feature.
Added plugin musepack with 1 feature.
Added plugin flac with 3 features.
Added plugin dvdec with 1 feature.
Added plugin gstaf with 3 features.
Added plugin videoflip with 1 feature.
Added plugin tcp with 7 features.
Added plugin synaesthesia with 1 feature.
Added plugin smoothwave with 1 feature.
Added plugin rmdemux with 1 feature.
Added plugin qtdemux with 1 feature.
Added plugin mpegstream with 4 features.
Added plugin system_encode with 1 feature.
Added plugin modplug with 1 feature.
Added plugin mng with 2 features.
Added plugin mixmatrix with 1 feature.
Added plugin goom with 1 feature.
Added plugin flxdec with 1 feature.
Added plugin gstequalizer with 1 feature.
Added plugin dtsdec with 1 feature.
Added plugin cutter with 1 feature.
Added plugin audioscale with 1 feature.
Added plugin gstaudioconvert with 2 features.
Added plugin apetag with 1 feature.
Added plugin adder with 1 feature.
Added plugin esdsink with 2 features.
Added plugin ossaudio with 3 features.
Added plugin alsa with 3 features.
Added plugin riff with 0 features.
Added plugin wavparse with 1 feature.
Added plugin ogg with 6 features.
Added plugin matroska with 2 features.
Added plugin cdxaparse with 2 features.
Added plugin avi with 2 features.
Added plugin asf with 2 features.
Rebuilding user_registry (/home/endangst/.gstreamer-0.8/registry.xml) ...
Loaded 150 plugins with 301 features.
endangst@ubuntu:/$

---

