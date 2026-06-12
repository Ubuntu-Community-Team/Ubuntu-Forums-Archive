---
title: "last.fm player"
date: 2006-01-12
forum: General Help
---

### Post by mvaniersel on 2006-01-12
I just downloaded the latest version of last.fm payer from their website. It crashes as soon as I click the "listen now" button after selecting a radio station, with the following output:
```
Found "hw:Intel,0"
Supports 16 bit
Supports 32 bit
Supports samplerate 48000
Supports samplerate 96000
Supports samplerate 192000
Settings filename: /home/martijn/.config/last.fm/player.ini
Handshake: "session=xxxxxxxxxxxxxxxxxxx
stream_url=http://streamer1.audioscrobbler.com/last.mp3?Session=xxxxxxxxxxxxxxxxxxx
subscriber=0
framehack=0
base_url=ws.audioscrobbler.com
base_path=/radio"
Changing station!
Using ALSA!
Supports 32 bit
Supports 16 bit

RtApi: no devices found for given stream parameters:
    RtApiAlsa: error setting sample rate (44100) on device (hw:Intel,0): Invalid  argument.
    RtApiAlsa: error setting sample rate (44100) on device (hw:Intel,1): Invalid  argument.


*** glibc detected *** double free or corruption (fasttop): 0x0887a158 ***
Aborted

```

Anybody else experienced this problem? Is this a problem with the player, or could this be a hardware problem? Other than this I've had no problems with the sound card, for example I can listen to mp3s with Rythmbox just fine. 

The soundcard is listed as a "CMI9880 Digital ALSA playback device" in the device manager.

---

### Post by mvaniersel on 2006-01-13
Nobody? Well let me ask a different question then: Has anybody successfully used the [last.fm]("http://www.last.fm/") player, linux version with Breezy?

---

### Post by 23meg on 2006-01-13
It works for one of my audio devices, and fails with the other. Did you try using it with OSS (you should be able to change it in its options)?

---

### Post by mvaniersel on 2006-01-13
Thanks, I didn't know you could do that.

With OSS it works, but it is far from perfect. I hear music, but there is a lot of noise in the background that I didn't experience under windows, and neither with Rhythmbox. Do you know a way to find out if this a problem with OSS or with the player?

---

### Post by 23meg on 2006-01-13
What kind of noise is it? Continuous hissing, or like stutters and cuts in the audio being played, or neither? If it's a hiss your microphone volume may be turned up; try muting it in the mixer. 

Also see if you get the same noise when you use OSS in other audio apps.

---

### Post by mvaniersel on 2006-01-13
Neither, it's a crackling noise, like listening to an old record player. 

I've tried the XMMS player both with ALSA and with OSS, the sound quality is good with both. The crackling doesn't seem to be caused by OSS. 

With OSS the sound is way too loud though, and I seem to be unable to put the volume down with the volume control or with the volume slider in XMMS. Also in last.fm the sound is way too loud, initially, but with last.fm you adjust the volume of the stream itself. So the loud volume seems to be an OSS problem. Perhaps the driver is bad after all.

edit: as you may have noticed, I'm a noob with ubuntu especially with sound. I have no idea what the difference is between ALSA and OSS :p

---

### Post by 23meg on 2006-01-13
It's most likely a buffer size issue; I don't have the player installed right now so I can't check but see if you have a "buffer size" option anywhere, and if it's there try using a different buffer size.

If you can't find a solution, do a search in the last.fm forums and/or post your problem there; you'll find lots of people using the Linux version there and they know the technical details of the player better.

---

### Post by mvaniersel on 2006-01-13
No, there is no buffer size option. 

I'll go and ask on the last.fm forum, thanks for your help.

---

### Post by malmjako on 2006-03-08
I experiense this crackling sound as well, a lot using v 1.1.4, a bit less with v 1.0.1. Did you find a solution? I've tried to do a proxy thingy with lastfmproxy ([http://vidar.gimp.org/lastfmproxy/](http://vidar.gimp.org/lastfmproxy/) ) and with the built-in function in v 1.1.4, but no media player seems to be able to connect. They just freeze.

---

### Post by mvaniersel on 2006-03-15
No, I didn't find a solution. At the last.fm forum I didn't get any response, except from people with the same problem. I'm simply doing without last.fm now.

---

### Post by firecat53 on 2006-03-15
I do have the Last.fm player working fine in Breezy, I  believe with ALSA.  I'll have to check when I go home tomorrow (don't have my laptop with me today).  It's an older Dell Inspiron laptop, so I can't imagine it would be a sound card issue. I'll look at all my settings and see if I can tell you something useful :)  Did you already check all the dependencies, just to make sure? I don't remember if there were any or not, but it'd be worth a look.

Scott

---

### Post by gorkhal on 2006-03-15
[QUOTE=firecat53]I do have the Last.fm player working fine in Breezy, I  believe with ALSA.  I'll have to check when I go home tomorrow (don't have my laptop with me today).  It's an older Dell Inspiron laptop, so I can't imagine it would be a sound card issue. I'll look at all my settings and see if I can tell you something useful :)  Did you already check all the dependencies, just to make sure? I don't remember if there were any or not, but it'd be worth a look.

Scott[/QUOTE]

Same here, works great with ALSA on breezy, i just untarred it into a temp directory, works very nice, great app and a most refreshing way of listening to music.

If your Last.fm player will not work correctly, make sure you have version 1.1.4 and then set the player to use an external media player (u'll find it under options), the player will then provide you with a local url, something like this....

[http://localhost:11111](http://localhost:11111) (example port number)

and then you can use XMMS to listen to the the local stream generated by the Last.fm player, works great, I am trying to get it to stream with Quod Libet, no luck yet.

hope this helps....:D

---

### Post by Zeroangel on 2006-03-15
Yeah, the built in 'use external player' option sucks.

I installed the last.fm proxy (the python version) and it runs like a dream!

---

