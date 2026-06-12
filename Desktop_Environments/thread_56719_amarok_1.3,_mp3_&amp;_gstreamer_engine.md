---
title: "amarok 1.3, mp3 &amp; gstreamer engine"
date: 2005-08-13
forum: Desktop Environments
---

### Post by yhotg on 2005-08-13
hi
i wanted to know how to get amarok to play mp3 with gstreamer engine
i was using amarok 1.2 with xine engine and all went alright , but now only can play .ogg files.

thanks
yhotg

---

### Post by hammett111 on 2005-08-14
Have you downloaded the gstreamer engine from kynaptic/synaptic?

---

### Post by yhotg on 2005-08-15
yes thank u.

amarok's now playing all my music files.
i did kind of went installing all the gstreamer files till amarok started working. 
I'm sure that i must have a lot of gstreamer stuff that i don't need but now is working lol

yhotg

---

### Post by Cybolic on 2005-09-21
[I]I'm having problems though...

At first when I installed Amarok, I couldn't play MP3's. Then I followed a guide somewhere that said that I should remove (or rename) the ffmpeg gstreamer files (in /usr/lib/gstreamer-0.8) and run gst-register.
After starting Amarok after that, it still complained that gstreamer couldn't play MP3's, but had no problem actually playing some - but now after I've rebooted, I can't play MP3's again?!

...I find this very odd... and quite annoying since I'm begining to like Amarok...

Does anyone have any clue as to why and what's happening?[/I]

Sorry! Nevermind... I'm running Breezy, so this isn't really the right place....

---

### Post by yhotg on 2005-09-21
[QUOTE=Cybolic][I]I'm having problems though...

At first when I installed Amarok, I couldn't play MP3's. Then I followed a guide somewhere that said that I should remove (or rename) the ffmpeg gstreamer files (in /usr/lib/gstreamer-0.8) and run gst-register.
After starting Amarok after that, it still complained that gstreamer couldn't play MP3's, but had no problem actually playing some - but now after I've rebooted, I can't play MP3's again?!

...I find this very odd... and quite annoying since I'm begining to like Amarok...

Does anyone have any clue as to why and what's happening?[/I]

Sorry! Nevermind... I'm running Breezy, so this isn't really the right place....[/QUOTE]

did u tried installing:
gstreamer0.8-mad - MAD MPEG audio decoder plugin for GStreamer
that's my apt-cache search ....
i installed a lot of codecs till i got to thatone and then all went nice and fine.
i don't know yet no thing about Breezy but maybe is the same codec right? it should be, is like logic right?

or maybe is this one:
gstreamer0.8-plugins - All GStreamer plugins

---

### Post by Cybolic on 2005-09-21
The thing is, I have **everything** conserning gstreamer installed, even the ruby bindings despite I don't need them.... I searched for "gstreamer" in Synaptic and installed everything, and trying the command line example from Amarok's documentation on how to test if gstreamer can play back MP3s works perfectly... muine and rythmbox can play MP3s as well...

...I don't get it...

---

### Post by yhotg on 2005-09-21
[QUOTE=Cybolic]The thing is, I have **everything** conserning gstreamer installed, even the ruby bindings despite I don't need them.... I searched for "gstreamer" in Synaptic and installed everything, and trying the command line example from Amarok's documentation on how to test if gstreamer can play back MP3s works perfectly... muine and rythmbox can play MP3s as well...

...I don't get it...[/QUOTE]

when in amarok, on the settings ---> configure amarok-----> engine
did u put gstreamer, right?
down that u have the output plugin. Did u tried with different plugins? i use alsa with xine, but i remember that i needed something like ossconfig or oss ... in order to listen the mp3s

i think...

---

### Post by Cybolic on 2005-09-21
I tried the Xine engine, and that worked beautifully, but just to test I changed back to the gstreamer engine and selected "autoaudiosink" as the output, and now MP3 works again... odd.

I'm not sure if MP3s work now because I had enabled the Xine engine previously, or because I selected the "autoaudiosink" output, but it works now.

Thanks for your help yhotg!

---

### Post by Cybolic on 2005-09-21
No, nevermind.

After playing 1 track, Amarok crashed and after starting it again, gstreamer once again couldn't play MP3s.... oh well, at least the Xine engine works - guess I'll just have to live without SIDs and MODs for a while....

---

### Post by yhotg on 2005-09-21
[QUOTE=Cybolic]No, nevermind.

After playing 1 track, Amarok crashed and after starting it again, gstreamer once again couldn't play MP3s.... oh well, at least the Xine engine works - guess I'll just have to live without SIDs and MODs for a while....[/QUOTE]

what are SIDs and MODs????

---

### Post by Cybolic on 2005-09-21
SID files are a sort of MIDI for Commodore 64, and MOD (module) files are music files typically from the Amiga ;)

---

