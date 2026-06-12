---
title: "Amarok - playing AACPlus streams"
date: 2006-06-18
forum: Desktop Environments
---

### Post by lzap on 2006-06-18
Hello,

I would like to listen AACPlus encoded radios in Amarok in Dapper Drake. Is it possible? It seems the only one application capable of playing this type of stream is VLC.

Amarok, my favourite player, is not able to read it and play it. I use the default binary (it uses the xine framework).

Thanks for help

---

### Post by Jucato on 2006-06-18
Are you able to play MP3's using Amarok? If so, you should also be able to play AAC/AACPlus formats. If not, you have to install the *libxine-extracodecs* package from the dapper multiverse repository. That's all that Amarok needs to play any restricted formats (except WMA/WMV).

I think the only problem would be that you are running Ubuntu, right? I'm not sure how it should go, since Ubuntu requires multiple libraries for restricted formats, while Kubuntu only needs libxine-extracodecs.

---

### Post by lzap on 2006-06-18
Yes I am running Ubuntu. Well, I have xine-extracodecd installed along with all these gstreamer ugly codecs, win32codecs etc. Amarok plays mp3 files and streams, but not AACPro.

Can somebody test one stream from DIGITALLY IMPORTED radio? [www.di.fm](www.di.fm)

Strange thing is I cannot play either on di.fm or the default streams from the preinstalled audio library in Amarok. I get "Not authorized" message...

---

### Post by lzap on 2006-06-18
I got this:

Access was denied for the URL: [http://160.79.128.40:7018/](http://160.79.128.40:7018/)
xine parameters: [http://160.79.128.40:7018/](http://160.79.128.40:7018/)

Trying to play [http://www.di.fm/aacplus/drumandbass.pls](http://www.di.fm/aacplus/drumandbass.pls)

---

### Post by ceros on 2006-06-29
Take a look at the bug report [here]("http://launchpad.net/distros/ubuntu/+source/xine-lib/+bug/50734"). The problem is with xine. I suggest compiling xine from source.

---

### Post by Jucato on 2006-07-02
I'm not sure if this will work 100%, but I might have found a bit of a workaround on how to play AACplus streams from [www.di.fm](www.di.fm), at least on some streams.

You have to download the 24k AACplus playlist (.pls) and the Add it to Amarok. Then you'll be able to connect to and play the streams.

@ceros: thanks for the bug link. One of the devs posted on July 1 that there will be a fix for it soon.

---

