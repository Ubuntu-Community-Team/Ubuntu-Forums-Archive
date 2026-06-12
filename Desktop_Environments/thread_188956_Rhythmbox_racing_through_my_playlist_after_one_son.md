---
title: "Rhythmbox racing through my playlist after one song"
date: 2006-06-04
forum: Desktop Environments
---

### Post by tph on 2006-06-04
Yesterday I upgraded to Dapper and then installed new codecs, reconfigured alsa and got my sound working again, but now rhythmbox stopped working normally. When I launch rhythmbox it works fine, and play one song, but after that song it races through my list, playing the first split second of every song. If I shutdown rhythmbox and start it again I can play one song then it's back to racing through my playlist.
When I start rhythmbox from the console I get the message
"*(rhythmbox:7198): GStreamer-CRITICAL **: gst_bus_source_dispatch: assertion `message != NULL' failed*" after I close rhythmbox.
The number behind "rhythmbox:" seems to increase with how long I let rythmbox race through my playlist.

I tried to download the most recent version of rhythmbox (found a link on this forum), but it didn't fix anything.

So anyways, anyone know a possible solution for this problem?

(if it's of any interest, I have a Intel High Definition Audo integrated sound card)

---

### Post by Harold P on 2006-06-04
[quote=tph]Yesterday I upgraded to Dapper and then installed new codecs, reconfigured alsa and got my sound working again, but now rhythmbox stopped working normally. When I launch rhythmbox it works fine, and play one song, but after that song it races through my list, playing the first split second of every song. If I shutdown rhythmbox and start it again I can play one song then it's back to racing through my playlist.
When I start rhythmbox from the console I get the message
"*(rhythmbox:7198): GStreamer-CRITICAL **: gst_bus_source_dispatch: assertion `message != NULL' failed*" after I close rhythmbox.
The number behind "rhythmbox:" seems to increase with how long I let rythmbox race through my playlist.

I tried to download the most recent version of rhythmbox (found a link on this forum), but it didn't fix anything.

So anyways, anyone know a possible solution for this problem?

(if it's of any interest, I have a Intel High Definition Audo integrated sound card)[/quote]
I get the same thing, but mine looks a little more complicated:

```
harold@ubuntu:~$ rhythmbox

(rhythmbox:5355): Rhythmbox-WARNING **: Unable to start mDNS browsing: MDNS service is not running
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3

(rhythmbox:5355): Rhythmbox-WARNING **: Unable to stop mDNS browsing: MDNS service is not running

(rhythmbox:5355): GStreamer-CRITICAL **: gst_bus_source_dispatch: assertion `message != NULL' failed
harold@ubuntu:~$

```

It it gives that message on each song, and just keeps going; leaving a red marker on the side of each song like this (see attachment):

---

### Post by Harold P on 2006-06-04
Here's an animated version of what mine is doing...

[IMG]http://img70.imageshack.us/img70/2618/ahhh1ed.gif[/IMG]

---

### Post by tph on 2006-06-04
I think "** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3" is beacuse of a missing codec, install all the gstreamer0.10-codecs you need ([https://wiki.ubuntu.com/RestrictedFormats?highlight=%28RestrictedFormats%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28RestrictedFormats%29))
I also removed the mDNS-error by installing some programs via synaptic (searched for mDNS)

---

### Post by Lussarn on 2006-06-05
I have the same condition (racing through playlists) on an updated breezy->dapper, I've noticed rhytmbox does work if I create a new user. Which would suggest something is wrong in either a user config file or a gnome registry key. I have not found a sollution though.

---

### Post by tph on 2006-06-05
Ok, it seems it's a problem with gstreamer, at least that's what Quod Libet said when I tried to use it instead of rhythmbox.
Quod Libet plays one song ok too, but it refuses to play any other songs until I restart the program. I've re-installed the gstreamer0.10-packs and removed all the old ones but nothing works.
I've filed a bug and hope it'll get a fix to the problem.
As a temporarily fix I'm using totem (totem-xine) to play my music.

---

### Post by Jindro on 2006-06-14
Lussarn:

I can confirm the same behavior on one of my upgraded Dapper from Breezy.
I reinstalled gstreamer - no success.


Let´s try your suggestion

---

### Post by dailer on 2006-07-28
Hi,
i found a solution for this problem. You have to change the output plugin in gstreamer-properties to OSS. It seems to be a problem of alsa or the alsa plugin of gstreamer.

---

