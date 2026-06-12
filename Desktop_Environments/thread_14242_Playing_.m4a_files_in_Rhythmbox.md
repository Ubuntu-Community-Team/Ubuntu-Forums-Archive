---
title: "Playing .m4a files in Rhythmbox"
date: 2005-02-05
forum: Desktop Environments
---

### Post by QzarBaron on 2005-02-05
Most of my music I ripped using iTunes and it made it into .m4a format. I tried opening them in both XMMS and Rhythmbox(although I prefer Rhythmbox for the playlist feature) and neither would open them. 

Is there a plugin I can install to make them work in Rhythmbox or is there a way I can convert them to .wav so I can then convert them to .ogg?

---

### Post by valadil on 2005-02-05
As of now there is no gstreamer (backend for rhythmbox) m4a plugin in apt.  I don't know if one even exists.

You should be able to play them in xmms though.  The mp4 plugin (which is in apt) might be able to handle those, though I'm not positive.  Once you get them playing in xmms you can convert them to wav with the disk writer output plugin that comes with xmms.

---

### Post by Hackmo on 2005-02-05
> You should be able to play them in xmms though. The mp4 plugin (which is in apt) might be able to handle those, though I'm not positive. Once you get them playing in xmms you can convert them to wav with the disk writer output plugin that comes with xmms.

What's the name of the plugin that will play them in xmms?

---

### Post by Phreakazoid on 2005-02-05
[QUOTE=Hackmo]What's the name of the plugin that will play them in xmms?[/QUOTE]

xmms-faad

Should also be possible to play .m4a files in rhythmbox if you install the gstreamer-faad plugin (not sure if there is an apt repository with that).

---

### Post by Vince on 2005-02-06
Actually MoreAmp will play your iTunes library. I had the same problem I've ripped all my CDs to Apple Lossless (aka LPAC/ACC ALS) and I needed a way to play them on my friend's linux computer.

I think XMMS has a FAAD2 library plug-in for it as well. However the only player I've actually got working is MoreAmp.

---

### Post by QzarBaron on 2005-02-06
This seems really complicated... I can't find the apt packages for xmms-faad or MoreAmp. Is there a way I can convert these into .wav so I can later turn them into .ogg or something?

Well Xine seems to be able to play them... and I know you can have Rhythmbox use Xine instead of GStreamer... but how do you do that?

Oh and it would still be much easier just to turn these into .ogg

---

### Post by QzarBaron on 2005-02-06
Nevermind about my problem. I found a really nice Windows app called dBpowerAMP and converted my entire library to mp3(so I could listen to music in Linux and Windows). It was a long and labourious process but I have it all working now.

---

### Post by jallen7usa on 2005-02-15
I was searching around for aac support in Ubuntu yesterday and wasn't able to find any of the packages (faad etc...).  Tonight I added the following to my sources.list to install another program and decided to check for aac support again.

```

deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

```

An
```
apt-cache search faad
``` 
returned 
```
xmms-mp4
```  

I installed it and now my m4a's are playing beautifully!

---

### Post by Ubuntu_User on 2005-02-23
Don't convert between lossy audio formats like mp4, mp3 and Ogg Vorbis. You will loose quality. If you have files in Apples proprietary lossless format you can convert them to wave files and then to the free and open [FLAC](http://flac.sourceforge.net/)  format which can be played in any decent audio player.

---

### Post by ChaperonNoir on 2005-03-28
You can't imagine the quality loss from  AAC 128 to MP3  [-X 

Thats why ill be patient, and wait for a way in linux to play these files.

---

### Post by Reb on 2005-04-06
gstreamer0.8-faa[dc] don't work for Rhythmbox .m4a. I would truthfully PAY for this to work. I like RB and hate (with a dark, fiery passion) VLC for music.

---

### Post by mostwanted on 2005-04-06
[QUOTE=Reb]gstreamer0.8-faa[dc] don't work for Rhythmbox .m4a. I would truthfully PAY for this to work. I like RB and hate (with a dark, fiery passion) VLC for music.[/QUOTE]

I have it working, playing Beck - Guero in AAC right now.

The package from marillat is broken, but the one in gismo is not.

---

### Post by Reb on 2005-04-06
gismo? I don't have that repository.

---

### Post by Reb on 2005-04-06
Come onnn... make my day!

---

### Post by SKLP on 2005-04-08
the debs for libfaad and gstreamer0.8-faad from [https://fuware.net/pymusique/](https://fuware.net/pymusique/) seems to work with hoary...
however just in rhythmbox, not in muine (which is what i prefer and use) :(

---

### Post by SKLP on 2005-05-03
anyone got an updated muine deb to fix this? getting really bored with having to use the horrible rhythmbox just to play SOME of my music, the AACs

---

### Post by abbot on 2005-05-05
[QUOTE=SKLP]the debs for libfaad and gstreamer0.8-faad from [https://fuware.net/pymusique/](https://fuware.net/pymusique/) seems to work with hoary...
however just in rhythmbox, not in muine (which is what i prefer and use) :([/QUOTE]

[QUOTE=SKLP]anyone got an updated muine deb to fix this? getting really bored with having to use the horrible rhythmbox just to play SOME of my music, the AACs[/QUOTE]

sorry i cant help you with muine, but thanks for the link.  those work nicely with rhythmbox.

---

### Post by Reb on 2005-08-30
With an update to Breezy tonight, gstreamer programs now play aac (.m4a) files fine.

---

### Post by Thermos on 2005-09-19
I can play some m4a files in rhythmbox, but should point out that these files are ones downloaded from a free podcast feed.  I can't play the ones I've bought through the iTunes music store though.

Anyone else witness something like this, or are you able to play ALL m4a files?

---

### Post by brian g on 2005-10-27
[QUOTE=Thermos]I can play some m4a files in rhythmbox, but should point out that these files are ones downloaded from a free podcast feed.  I can't play the ones I've bought through the iTunes music store though.

Anyone else witness something like this, or are you able to play ALL m4a files?[/QUOTE]
[FairPlay](http://en.wikipedia.org/wiki/FairPlay) is hardly fair

---

### Post by macarroni on 2006-04-20
I can play apple lossless files in Rhythmbox, I installed a lot of things so I'm not sure which of them was the one that enabled me to play them.

I think it was this: [http://packages.ubuntu.com/breezy/libs/gstreamer0.8-ffmpeg]("http://packages.ubuntu.com/breezy/libs/gstreamer0.8-ffmpeg")

---

### Post by shutupimpoor on 2006-05-05
with Universe and Multiverse repositories enabled (i think)

then administration > synaptic package manager 
and get all the gstream files (particularly faad, ffmpeg, and lame)

i am not positive if thats the step i took to finally get my .m4a files to work in rhythmbox, but hopefully it helps. I am still newb so forgive me if I used incorrect words. the files still don't run in xmms or beep, but rhythmbox will do

---

### Post by Ted_Smith on 2006-05-06
jallen7usa

In your post on the first page of this thread, when you say you 'installed it' (xmms-MP4), can you tell me how, and from where? I have found [this link]("http://packages.ubuntulinux.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Ff%2Ffaad2%2Fxmms-mp4_2.0.0%2Bcvs20040908%2Bmp4v2%2Bbmp-0ubuntu3_i386.deb&md5sum=2549505265b72424ef32b4269cfeaf18&arch=i386&type=main") titled Download Page for xmms-mp4_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3_i386.deb on Intel x86 machines but whenever I download the deb file and try to run it Ubuntu can't do it? It says 'Archive type not supported'.

I am a whole stash of m4a files that I want to play but can't. Can you help clarify for a Linux Newb? 

Thanks

Ted

---

### Post by Ted_Smith on 2006-05-06
I my giddy god - if you haven't heard of it, just download and install Cross Over Office by Code Weavers ([www.codeweavers.com)](www.codeweavers.com)). I've installed it using the HTTP download (there's a choice of bittorrent, FTP or HTTP), I then just su'd to root, navigated to the where I had downloaded the sh file, ran 'sh NameOfTheFile.sh', and it installed no trouble. You then choose what you want to install (in my case iTunes, but there's about 30 apps) - it installs it in a virtual kind of way, and at the end you have an iTunes icon on your desktop. Double click it, and it just looks iTunes - it is iTunes, but running in Linux. Happily added my m4a files from my drive, and playing them. 

Fantastic. After 30 days you have to pay about $40 (£28 roughly) which I think I'll do when my trial expires. 

Ted

---

### Post by ericartman on 2007-08-13
if you want to use crossover make sure you don't update your ipod as the last two updates makes crossover unusable. Think functionality fails at 6.0 at least according to their site, I have 7.0 and it doesn't work. 

Cart

I still rip Acc to Mp3, unless I use a good quality headphone the difference isn't much to these 50 plus old ears.  Too many rock concerts and bullets I guess, lol.

---

