---
title: "DVD:RIP + official divx5: not possible anymore?"
date: 2005-11-22
forum: Desktop Environments
---

### Post by suoko on 2005-11-22
Hi,

after I installed the divx5.0.5 codec from divx.com, I tried to encode some video from a DVD but I get the following error message.
Is there a solution to this or am I forced to use ffmpeg + mpeg4?

[export_divx5.so] v0.1.8 (2003-07-24) (video) DivX 5.xx | (audio) MPEG/AC3/PCM
[export_divx5.so] *** Warning: DivX is broken and support for it is ***
[export_divx5.so] *** obsolete in transcode. Sooner or later it  ***
[export_divx5.so] *** will be removed from transcode. Don't use ***
[export_divx5.so] *** DivX. Use xvid or ffmpeg -F mpeg4 instead ***
[export_divx5.so] *** for all your mpeg4 encodings. ***
[transcode] warning : failed to init DivX 5.0 Codec

---

### Post by michael_salcher on 2005-11-22
divx 5 seems to be not supported. what's wrong with using xvid?

---

### Post by suoko on 2005-11-22
Nothing. It's just a question of choice.

---

### Post by Ikitt on 2006-09-27
> **suoko said:**
> Hi,
after I installed the divx5.0.5 codec from divx.com, I tried to encode some video from a DVD but I get the following error message.
Is there a solution to this or am I forced to use ffmpeg + mpeg4?

[export_divx5.so] v0.1.8 (2003-07-24) (video) DivX 5.xx | (audio) MPEG/AC3/PCM
[export_divx5.so] *** Warning: DivX is broken and support for it is ***
[export_divx5.so] *** obsolete in transcode. Sooner or later it  ***
[export_divx5.so] *** will be removed from transcode. Don't use ***
[export_divx5.so] *** DivX. Use xvid or ffmpeg -F mpeg4 instead ***
[export_divx5.so] *** for all your mpeg4 encodings. ***
[transcode] warning : failed to init DivX 5.0 Codec
Yes, we are going to deprecate divx5 support in transcode. Supporting divx5.0x is a pretty painful process, codec itself has known bugs and it doesn't offer more (under linux) than libre counterparts.
Divx6 is a pretty different story, it looks much better than divx5, an
it seems it has more features, less bugs and better docs. Anyway, we prefer
to focus on freesoftware formats/codecs. Supporting divx6 has just a very low priority. Patches welcome of course ;)

PS: sorry for bumping an old thread, I've seen posting date only after "send" button pressed. :(

---

