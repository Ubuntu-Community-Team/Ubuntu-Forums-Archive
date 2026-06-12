---
title: "DVDs with totem-gstreamer"
date: 2005-03-22
forum: Desktop Environments
---

### Post by Remm on 2005-03-22
Chapter navigation, menu access, etc, does not work for me, without any error shown. The first chapter of DVDs (logos and FBI warnings, how cool is that ? ;) ) work very well, however.

I have the full gst plugin suite installed, as well as dvdnav4, dvdread3 and dvdcss2.

Is this supposed to work ? What am I doing wrong ?

---

### Post by cdhotfire on 2005-03-22
try totem-xine works for me. :-)

---

### Post by Remm on 2005-03-22
[QUOTE=cdhotfire]try totem-xine works for me. :-)[/QUOTE]

Yes, I assume it would work (having explicit documentation pages, etc), but my post was more something like: isn't totem-gst (the default) supposed to do DVDs as well ? From what I understand it should, so assuming I am not doing anything wrong, it's a bug.

---

### Post by j_baer on 2005-03-22
Remm,

Using Totem-Gstreamer has been problematic for me with jumpy playback and out of sync audio. As such I have returned to Xine which works great.

There is also a thread in the how-to section that embeds Totem into Firefox for a really nice web experience.

That said, I really like the quality of Gstreamer-audio and wouldn't it be nice if the same magic worked for video.

Cheers ...

---

### Post by darrenadams on 2005-03-22
Currently GStreamer doesn't support DVD navigation as well as Xine does (but, as you've seen, it's getting there!), so the if you do want to play DVD's in totem, install the totem-xine package instead

---

### Post by Remm on 2005-03-22
[QUOTE=darrenadams]Currently GStreamer doesn't support DVD navigation as well as Xine does (but, as you've seen, it's getting there!), so the if you do want to play DVD's in totem, install the totem-xine package instead[/QUOTE]

Ok. This could be a lot more explicit, though ;)
For example, playback with totem-gst is also choppy with some formats.

---

### Post by darrenadams on 2005-03-22
[QUOTE=Remm]Ok. This could be a lot more explicit, though ;)
For example, playback with totem-gst is also choppy with some formats.[/QUOTE]

The comment about GStreamer's DVD capabilities? Well, I got that from a comment made on FootNotes regarding a GStreamer release [http://gnomedesktop.org/node/2108#comment-33938](http://gnomedesktop.org/node/2108#comment-33938). It's probably a bad example because the comment is a couple of months old now, and DVD support (as well as support for other formats) has probably come along since then. For the time being though I'll use totem-xine and will keep checking in on totem-gstreamer from time to time.

---

### Post by Remm on 2005-03-22
[QUOTE=darrenadams]The comment about GStreamer's DVD capabilities? Well, I got that from a comment made on FootNotes regarding a GStreamer release [http://gnomedesktop.org/node/2108#comment-33938](http://gnomedesktop.org/node/2108#comment-33938). It's probably a bad example because the comment is a couple of months old now, and DVD support (as well as support for other formats) has probably come along since then. For the time being though I'll use totem-xine and will keep checking in on totem-gstreamer from time to time.[/QUOTE]

It would be logical that DVD support didn't improve much since Jan since they were probably in semi-freeze for the Gnome 2.10 release.

---

