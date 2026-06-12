---
title: "Sound Juicer is ripping MP3 files"
date: 2007-01-12
forum: Desktop Environments
---

### Post by DSA on 2007-01-12
Hi there,

I have been trying to get Sound Juicer to rip files on MP3 format. I have followed up a number of threads and tried different configurations. 

I am using Edgy 6.10 - SoundJuicer 2.16.1 and the GStreamer codecs. 

On the MP3 profiles I tried the following configurations:

Test 1 > Audio/x/raw-int,rate=44100,channels=2 ! lame name=enc bitrate= 192
Test 2> Audio/x/raw-int,rate=44100,channels=2 ! lame name=enc bitrate=196
Test 3> Audio/x/raw-int,rate=44100,channels=2 ! lame name=enc bitrate=192 ! id3v2mux
Test 4> Audio/x/raw-int,rate=44100,channels=2 ! lame name=enc preset=1001 ! id3v2mux
Test 5> Audio/x/raw-int,rate=44100,channels=2 ! ugly  name=enc bitrate=192 
Test 6> Audio/x/raw-int,rate=44100,channels=2 ! ugly  name=enc bitrate=192 ! id3v2mux
Test 7> Audio/x/raw-int,rate=44100,channels=2 ! ugly  name=enc vbr=0 bitrate=192 ! id3v2mux

All of these tests create  a similar  60Mbytes file (for a 5.56 minutes song) that cannot be played by either the Totem player or the Rhytmbox player.  Other Mp3 that I have play fine by either of those.

Would anybody have any suggestions?

Thank you

DSA](*,)

---

### Post by chrisccoulson on 2007-01-12
Did you do it according to [this]("https://help.ubuntu.com/community/CDRipping#head-f109ee313aa77bf2997e6499584438e9f7691d58") wiki? I have followed this and seem to be able to rip MP3's fine.

The only thing I've noticed is that your syntax appears to be slightly different. The wiki shows:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=160 ! id3v2mux
```

as opposed to your:

```
audio/x/raw-int,rate=44100,channels=2 ! lame name=enc bitrate=192 ! id3v2mux
```

Try replacing the second '/' with a '-'.

---

### Post by DSA on 2007-01-15
Hi Chris,

Thank you for the reply.  I actually found that I had to enable GStreamer with the Sinaptic package manager. After I enable it Sound Juicer started to work.  The following syntax works well.

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=192 ! id3v2mux

Thank you again.

Daniel

---

### Post by Muffy on 2007-07-17
Hmmm... I've tried this (amongst a bunch of others):

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=192 ! id3v2mux

The tracks are ripped alright, but they're way too big to be mp3.  For example, I just ripped a 3m 25s track that cashed in at  34.5Mb which just doesn't seem right for an mp3.  Any suggestions?

---

### Post by Muffy on 2007-07-17
OK never mind; one of these fixed up my problem:

```
sudo apt-get install gstreamer0.10-plugins-ugly
```

---

### Post by RobMBaker on 2007-07-24
I'm using a similar pipeline to rip to VBR mp3s, but for some reason no ID3 tags are created on my ripped files - even though I'm using id3v2mux.

Any way to check if I have the right package(s) installed, or would it give an error message if I tried to use id3v2mux without actually having it installed?

edit: I mean, my mp3s have the right metadata when viewed in Nautilus (Properties; then the Audio tab) but when I'm tagging files with Audio Tag Tool, they all have null ID3v2 tags, and no v1 tags.

---

### Post by yaidiot! on 2007-09-04
It's creating mp3id v2.4 tags. ATT uses v2.3 IIRC.

Try ripping with Grip, or tag editing with Ex Falso.

---

