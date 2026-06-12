---
title: "totem gstreamer plugin problem"
date: 2006-06-01
forum: Desktop Environments
---

### Post by weresheep on 2006-06-01
Totem-gstreamer is rapidly turning into my nemesis!

I've been using Ubuntu since I tried Warty and loved it however, I have never been able to get totem-gstreamer to do anything useful with my media files. Every Ubuntu release I give it a quick try and then give up and install totem-xine, mplayer or VLC. But not today. I've just installed Dapper and I am determined to get totem-gstreamer to play my movies files.

So, what do I need to do to be able to play, e.g. mpeg 1 movie files with totem-gstreamer? What I've done so far is enable the universe repositories and install

    ffmpeg 
    gstreamer0.10-ffmpeg

but still no luck. Every time I try and play a movie file totem pops up a dialogue box saying...

"You do not have a decoder installed to handle this file type.
You might need to install the necessary plugins."

I've checked the MIME type of the files are correct (video/mpeg). Please, I am going mad here. What else do I need to do?

Many, many thanks to anyone that can help.

-weresheep

---

### Post by deadgobby on 2006-06-01
[QUOTE=weresheep]Totem-gstreamer is rapidly turning into my nemesis!

I've been using Ubuntu since I tried Warty and loved it however, I have never been able to get totem-gstreamer to do anything useful with my media files. Every Ubuntu release I give it a quick try and then give up and install totem-xine, mplayer or VLC. But not today. I've just installed Dapper and I am determined to get totem-gstreamer to play my movies files.

So, what do I need to do to be able to play, e.g. mpeg 1 movie files with totem-gstreamer? What I've done so far is enable the universe repositories and install

    ffmpeg 
    gstreamer0.10-ffmpeg

but still no luck. Every time I try and play a movie file totem pops up a dialogue box saying...

"You do not have a decoder installed to handle this file type.
You might need to install the necessary plugins."

I've checked the MIME type of the files are correct (video/mpeg). Please, I am going mad here. What else do I need to do?

Many, many thanks to anyone that can help.

-weresheep[/QUOTE]
 You need to install the codecs. Try Installing Automatix and see if that fixes the problem. Cause I just got done upgrading too and lost all of the codes and had to reinstall them by running Automatix. Now to get Mplayer working agian. Works fine for Firefox just fine.

---

### Post by BoyOfDestiny on 2006-06-02
[QUOTE=weresheep]Totem-gstreamer is rapidly turning into my nemesis!

I've been using Ubuntu since I tried Warty and loved it however, I have never been able to get totem-gstreamer to do anything useful with my media files. Every Ubuntu release I give it a quick try and then give up and install totem-xine, mplayer or VLC. But not today. I've just installed Dapper and I am determined to get totem-gstreamer to play my movies files.

So, what do I need to do to be able to play, e.g. mpeg 1 movie files with totem-gstreamer? What I've done so far is enable the universe repositories and install

    ffmpeg 
    gstreamer0.10-ffmpeg

but still no luck. Every time I try and play a movie file totem pops up a dialogue box saying...

"You do not have a decoder installed to handle this file type.
You might need to install the necessary plugins."

I've checked the MIME type of the files are correct (video/mpeg). Please, I am going mad here. What else do I need to do?

Many, many thanks to anyone that can help.

-weresheep[/QUOTE]

Enable mulitverse repos as well.

Get everything starting with gstreamer.10 (well not the -dev or document files). I used to hate totem. Now it's my most commonly used player for videos and DVD's. :)

---

### Post by blackjack6.21.91 on 2006-06-02
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

follow the instructions to install necessary codecs.  but i'm pretty sure totem-xine is better regardless

---

### Post by weresheep on 2006-06-02
Hi guys,

Thanks for the replies. I'm at work at the moment but I'll try your suggestions when I get home :-D 

I am a little confused in general about totem / gstreamer though. When I installed ffmpeg I used ffplay to play a bunch of my movie files to make sure it was working okay. I thought that installing the gstreamer0.10-ffmpeg plugin would make totem use ffmpeg for its decoding.

This obviously isn't the case so what does the gstreamer0.10-ffmpeg plugin do?

Thanks again.

-weresheep

---

### Post by uros678 on 2006-06-02
From the gstreamer homepage.. it reads...

*GStreamer FFmpeg plug-in contains one plugin with a set of elements using the FFmpeg library code. It contains most popular decoders as well as very fast colorspace conversion elements.*

If you wan't more info you can always try the ffmpeg home page.. I think it is ffmpeg.mplayer.hu or something like that...

best regards,
uros

---

### Post by Belibem on 2006-06-02
make sure you 've installed all those three packages
gstreamer0.10-plugins-good
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly

you need to have universe and multiverse repositories enabled. To do so type:
sudo gedit /etc/apt/sources.list
and uncomment (remove the # ) the corresponding lines

---

### Post by weresheep on 2006-06-02
I managed to get things working with totem and gstreamer after installing the bad and ugly packages. I'm still a little confused as to why I need to install the ugly plugins to get ffmpeg to work but at least I can now play my media files. 

Many thanks for the help.

-weresheep

---

### Post by dmizer on 2006-06-26
well, with this thread, i was actually able to get a streaming video to play. but i could only hear sound, no video displayed at all.  any ideas are appreciated.

yeah ... no totem dvd play either.

xine playes the dvd, but it's jumpy ... no skips like with bad dma, but jumpy like an old time black and white movie.

edit: got totem to work for streaming video ... kind of.  larger videos like at video.google.com are slow and skip alot, but smaller videos work fine.  anyway, i got it to work thanks to easy ubuntu: [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

---

