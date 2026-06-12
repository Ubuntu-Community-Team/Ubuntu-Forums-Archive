---
title: "Rip and encode CD's as MP3 320 KBPS Rhythmbox"
date: 2009-06-23
forum: Florida Team - US
---

### Post by aliencure on 2009-06-23
:confused: Hello all. I am wondering if there is a way to rip a CD in Rhythmbox but encode the MP3 files using 320 kbps constant bit rate (CBR). Any suggestions?

---

### Post by mlsquad on 2009-06-24
> **aliencure said:**
> :confused: Hello all. I am wondering if there is a way to rip a CD in Rhythmbox but encode the MP3 files using 320 kbps constant bit rate (CBR). Any suggestions?You have to go to Edit->Preferences->Music->Edit.  Highlight CD Quality, MP3 and then choose Edit.  In GStreamer pipelin you should have "audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux"  I'm not sure which settings to edit, probably vbr-quality.

---

### Post by flotoonie on 2009-12-30
Can anyone help and suggest what the new settings should be?

---

### Post by lukeiamyourfather on 2009-12-30
> **flotoonie said:**
> Can anyone help and suggest what the new settings should be?

What do you mean by "new" settings?

---

### Post by flotoonie on 2009-12-30
If I wanted 320 kbps what would I change in the settings that were posted earlier in the thread?

An earlier poster said that the vbr quality should be changed.  Should I change the 6?  If so what to?

Cheers

---

### Post by lukeiamyourfather on 2009-12-30
> **flotoonie said:**
> If I wanted 320 kbps what would I change in the settings that were posted earlier in the thread?

An earlier poster said that the vbr quality should be changed.  Should I change the 6?  If so what to?

Cheers

If you want a high quality rip (which it sounds like you do), use something else besides MP3 because its a lossy format no matter how high the bit rate is. Besides being lossy its also old and proprietary. FLAC would be a much better option because its a lossless format but is compressed (like a ZIP) so its smaller than the actual disc. Also its open source and free. It can be transcoded at any time to something else like an MP3 so an iPod can use it and the transode would be like it was coming from the original disc (since FLAC is lossless). Almost every audio player out there supports FLAC playback and most support FLAC ripping, even some portable players support FLAC.

As for the MP3 ripping, VBR 0 would be the highest quality, close to CBR 320 kbps but with a slightly smaller file. Use "man" to get the manual pages for a command like "man lame" to get all the details. If you don't have lame already then install it with "sudo apt-get install lame" and FLAC with "sudo apt-get install flac" if you want to try that too. Cheers!

---

### Post by alex.colpitts on 2009-12-30
you might want to get a faster cd drive, or just go into preferences and switch the sound quality

---

### Post by lukeiamyourfather on 2009-12-30
> **alex.colpitts said:**
> you might want to get a faster cd drive, or just go into preferences and switch the sound quality

What? Did you read the entire thread? Your post doesn't make any sense.

---

### Post by dantrevino on 2009-12-30
> **aliencure said:**
> :confused: Hello all. I am wondering if there is a way to rip a CD in Rhythmbox but encode the MP3 files using 320 kbps constant bit rate (CBR). Any suggestions?

Here is a thread with a few options listed.

[http://ubuntuforums.org/showthread.php?t=1112941](http://ubuntuforums.org/showthread.php?t=1112941)

Good luck.

Dan

---

### Post by Nat90 on 2010-01-02
Here's what you should put

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=320 ! id3v2mux
```

I recommend you use Sound Juicer though, here's a guide for 320 bitrate

[http://ubuntuhowtos.com/howtos/rip_audio_to_mp3 ]("http://ubuntuhowtos.com/howtos/rip_audio_to_mp3")

---

### Post by itnet7 on 2010-01-03
> **Nat90 said:**
> Here's what you should put

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=320 ! id3v2mux
```

I recommend you use Sound Juicer though, here's a guide for 320 bitrate

[http://ubuntuhowtos.com/howtos/rip_audio_to_mp3 ]("http://ubuntuhowtos.com/howtos/rip_audio_to_mp3")

Thanks for Posting that how to! I will also check it out... Plan on teaching my family to use sound juicer and if I can set it up for higher bitrates, so much the better!

Chris Crisafullii
FLorida Team Ubuntu LoCo
itnet7/#ubuntu-us-fl -- irc.freenode.net

---

### Post by inspiredminds on 2010-08-03
Hey all,

I would suggest RipperX. It can be found in the repository and can be installed using Synaptic(dependencies will be taken care of). I am using it for a week now and it is nice. 
You can choose from various bit rates including 128k, 256k and 320k(max).
can choose different VBR quality 
Can rip to mp3, ogg, flac
Has CDDB which can find track info online and attach tag n ids to the tracks
Has GUI and in few clicks you are good to go !!! 
I am using it on 10.04 and so far so good :D

---

### Post by peertje888 on 2010-10-12
And WHY THE F is MP3 not the default format for exporting a cd to your library? Majority of the people would want mp3, why is ogg the default for? Give me a break!

---

### Post by dr_hooride on 2010-10-23
Why use Sound Juicer or one of the many stand alone applications instead of say, Rhythymbox, Banshee or Exaile?  If the LAME encoder is what is used, shouldn't quality and settings be the same?  Still fairly new to this.  On my main desktop at work I still use iTunes for encoding and Mediamonkey for my tag editing/album art.  Trying to familiarize myself with some new stuff here.

---

### Post by leona on 2012-01-10
I have tried to use RipperX but couldn't figure out why it creates a WAV file first and then the created mp3 file had no ID3 tag info, looked nice, but its no Sound Juicer. :(

> **inspiredminds said:**
> Hey all,

I would suggest RipperX. It can be found in the repository and can be installed using Synaptic(dependencies will be taken care of). I am using it for a week now and it is nice. 
You can choose from various bit rates including 128k, 256k and 320k(max).
can choose different VBR quality 
Can rip to mp3, ogg, flac
Has CDDB which can find track info online and attach tag n ids to the tracks
Has GUI and in few clicks you are good to go !!! 
I am using it on 10.04 and so far so good :D

---

