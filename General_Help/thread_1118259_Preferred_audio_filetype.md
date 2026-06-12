---
title: "Preferred audio filetype?"
date: 2009-04-06
forum: General Help
---

### Post by ankspo71 on 2009-04-06
Hi,

I have been a linux user off and on for about 6 months now. I just said "so long" to windows when I found out I was unable to upgrade my processor after purchasing and installing Vista the other day. It was an OEM System Builder disk, which I thought could be used even if I need to continue to build my system ("system builder"). Boy was I wrong about that. 

Anyways, what is the default or most preferred audio format in Linux? is it .ogg? 


Thanks,
James. (A full time linux user now)

---

### Post by uc50_ic4more on 2009-04-06
.ogg Voribis (OGG is just a file container, Vorbis is the actual audio codec) is a good bet, as well a .flac, which is lossless and therefore of much higher quality, and more suited for archival (in my pinion).

---

### Post by ankspo71 on 2009-04-06
Thanks.

I was using a dual OS system, and used windows for gaming and music. Now that windows is out of the picture, I want to make the best of linux. My mp3's never sounded too good in linux so I want to re-rip them in linux for the first time.

Thanks for the help.
James

---

### Post by mb_webguy on 2009-04-06
According to this [2005 test]("http://www.listening-tests.info/mf-128-1/results.htm"), at a bitrate of 128kbit/s, the quality of the mp3, Ogg Vorbis, AAC (mp4), and wma formats are essentially the same.  That means for the most commonly used bitrate, sound quality shouldn't be a consideration when choosing a format.

Mp3 is the most common, primarily *because* it's the most common.  The mp3 format is supported by more devices and applications than any other.  As long as devices and applications tend to provide more support for mp3, people will tend to use mp3 more than other formats.

Many Linux users like Ogg Vorbis because both the container (Ogg) and codec (Vorbis) are free and open-source.  Practically all Linux applications support Ogg Vorbis for this reason.  A few commercial devices, in particular the SanDisk Sansa line of mp3 players, are starting to support Ogg Vorbis, but widespread adoption of the format is slow in coming.

Some people like the AAC format (such as used in the mp4 container and its variants), because it has better sound quality at higher bitrates than 128kbit/s.  It's also almost as widely supported by applications and devices as mp3.  However, the mp4 container and its variants support DRM, with which many Linux users have a problem -- if only that DRM'ed audio files can't currently be played on Linux.  Most people that use AAC audio do so because they're former Windows users who have a large media library of music downloaded from the iTunes store.

Like mp4, wma is almost as widely supported as mp3, but few Linux users use it.  Some people avoid it simply because it's a Microsoft-proprietary format.  Others avoid it because, like mp4, it supports DRM.  But most people don't use it simply because it's not a very popular format, even though it's well supported.

The flac format is also free and open-source, and is also a lossless format.  It's commonly used for archive purposes, but it's not as widely supported as the other formats previously mentioned, including Ogg Vorbis -- though again, it is supported by the SanDisk Sansa line of mp3 players.

So if you only want to play the music on your computer or on devices which support Ogg Vorbis or flac, then you may want to start using those formats.  Otherwise, you should probably stick with mp3.  The mp4 and wma formats should probably be avoided because they potentally have DRM (which you can't play on Linux), if for no other reason.

---

### Post by uc50_ic4more on 2009-04-06
If audio quality is a concern, and disk space is less of one, then FLAC is the best bet, in my opinion. It is lossless, meaning that is will sound exactly the same as the encoded file did.

If you need your encoded files to play on portable players and other devices, .mp3 would be the best bet, and encoding at a bitrate higher than 192kbps sounds OK, and 320kbps sounds pretty good. Since the files on (my wife's) iPod do not change often, I encode everything FLAC, and create .mp3's for her player.

---

### Post by ankspo71 on 2009-04-06
Thanks uc50_ic4more and MB_WebGuy,

Without the other OS, I now have a second hard drive available for storage, so size of the music files wouldn't be a problem for me.

Yes, my music files will be only used in linux. I don't have a ipod or anything like that.

I will go with ogg vorbis or flac... mainly because I fear one day Linux may become less interested in audio support for mp3.... since ogg is the preferred among linux users. I haven't been a linux user that long, but I have seen quite a few packages come and go already, in the repositories I mean.

Thanks for all of your help and information.
Take care,
James.

---

### Post by dtoronto on 2009-04-06
Yep .ogg sometimes .flac too

---

### Post by mb_webguy on 2009-04-06
> **ankspo71 said:**
> I will go with ogg vorbis or flac... mainly because I fear one day Linux may become less interested in audio support for mp3.... since ogg is the preferred among linux users. I haven't been a linux user that long, but I have seen quite a few packages come and go already, in the repositories I mean.

It's actually very unlikely that Linux (or rather it's applications) will ever stop supporting mp3s.  Linux is a community effort, and it will support whatever its users need it to support, because those users are the ones that create the software.  As long as there's even one Linux user that wants to use mp3s, there will be mp3 support.  It's actually more likely that Windows and Microsoft will stop supporting mp3 in favor of another format.

There are good reasons you might want to use Ogg Vorbis instead of mp3, but the fear that Linux will ever stop supporting mp3 isn't one of them.  Flac, on the other hand, is in a different category, as it's a lossless format.  For archival purposes, flac is definitely the way to go.

Also, you should keep in mind that converting from one lossy format to another will *always* result in a loss of quality.  Therefore, if you already have a large mp3 collection, there's *no* good reason to convert it to Ogg Vorbis unless you've suddenly decided to go 100% FOSS.

---

### Post by ankspo71 on 2009-04-06
Thanks, I think I needed to hear that about support for mp3, I'm feeling relieved now.

Currently I have somewhere around 650 mp3's, 128 bitrate, encoded by lame. They sound a little crackly, and have much less sound quality than they did in windows. 

Banshee is my favorite player, Alsa is my default driver (I think) and I have the required gstreamer codecs installed to play them. I find it odd that Last.Fm (the banshee plugin) sounds better than my own mp3's

Tonight I will listen to the actual music CD's and see if there is a sound quality difference (less crackly sounds), before I attempt to rip them.

Thanks again.
James.

---

### Post by uc50_ic4more on 2009-04-06
My thinking has always been that in some years from now, we'll be using uncompressed formats for lots of media, as storage, bandwidth and processing power will be capable of handling it. If you've got the storage, keep it lossless and essentially "first" generation quality.

---

### Post by logos34 on 2009-04-07
> **ankspo71 said:**
> Currently I have somewhere around 650 mp3's, 128 bitrate, encoded by lame. They sound a little crackly, and have much less sound quality than they did in windows. 

...

Tonight I will listen to the actual music CD's and see if there is a sound quality difference (less crackly sounds), before I attempt to rip them.


+1 for ogg vorbis (and/or flac if you have tons of disk space).

I highly doubt the 'crackly' sounds are caused by playback in linux...More likely the sound settings need adjusting (one common culprit is PCM level too high, causing what sounds like clipping).  So I wouldn't waste time re-ripping them (unless of course you'd like them in ogg vorbis format, my fav lossy.  128k is pretty low, even vbr, but if they're cbr then you definitely want to re-rip to ogg q5 maybe.)

---

### Post by SunnyRabbiera on 2009-04-07
.ogg vorbis and MP3 both perform well

---

### Post by megamania on 2009-04-08
> **uc50_ic4more said:**
> My thinking has always been that in some years from now, we'll be using uncompressed formats for lots of media, as storage, bandwidth and processing power will be capable of handling it. If you've got the storage, keep it lossless and essentially "first" generation quality.
I agree. In five years we will measure hard disk space by terabytes (as we did with gigabytes a few years ago) and we will be laughing at the size of our current mp3 files...

---

