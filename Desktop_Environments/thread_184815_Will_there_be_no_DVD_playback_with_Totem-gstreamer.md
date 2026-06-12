---
title: "Will there be no DVD playback with Totem-gstreamer?"
date: 2006-05-30
forum: Desktop Environments
---

### Post by temcat on 2006-05-30
Hi all,

as far as I can see there's still no gstreamer0.10-dvd plugin in repositories. Does it mean that Totem-gstreamer will not play DVD? Or is this plugin not needed anymore?

Restricted Formats Wiki says so, but somebody told me that the info in the wiki is old and Totem-gstreamer now does play DVD...

Thanks in advance!

---

### Post by wout.wepsait.com on 2006-05-30
same question here

---

### Post by John.Michael.Kane on 2006-05-30
i think what your looking for is this one gstreamer0.10-plugins-ugly it installs libdvdread3.


hope this helps.

---

### Post by Lord Illidan on 2006-05-30
Are there any reasons why not to use totem-xine? That can play dvds..

---

### Post by JoWilly on 2006-05-30
[QUOTE=SD-Plissken]i think what your looking for is this one gstreamer0.10-plugins-ugly it installs libdvdread3.
[/QUOTE]

 Yep and don't forget to do "sudo /usr/share/doc/libdvdread3/examples/install-css.sh" to instal support for encrypted dvds ;)

---

### Post by MetalMusicAddict on 2006-05-30
I thought the "DVD" plug-in allowed for menus and such? Im using totem-xine now but I plan to switch.

---

### Post by az on 2006-05-30
[QUOTE=Lord Illidan]Are there any reasons why not to use totem-xine? That can play dvds..[/QUOTE]
You need the w32codecs which are not licenced for redistribution.  They are essentially, stolen.

---

### Post by Video Toaster on 2006-05-30
[QUOTE=azz]You need the w32codecs which are not licenced for redistribution.  They are essentially, stolen.[/QUOTE]
Aren't they OK if you have a valid Windows license, though?

---

### Post by RAOF on 2006-05-30
[QUOTE=azz]You need the w32codecs which are not licenced for redistribution.  They are essentially, stolen.[/QUOTE]
Not for DVD playback, you don't.  I run AMD64 (so no w32codecs ;)), and **my** totem-xine plays DVDs just fine, thank you :).

You need w32codecs for slightly more exotic things than the mpeg2 found on DVDs.  (WMV3/Windows Media 9/VC-1/whatever else it's called, and some other things).

In short:  GStreamer 0.10 does not yet have a DVD-nav type element.  So, totem-gstreamer is not going to play your DVDs well.

---

### Post by Senori on 2006-05-30
GStreamer does (check out seamless.sf.net) but Totem hasn't implemented it yet.

---

### Post by az on 2006-05-30
> **RAOF]Not for DVD playback, you don't.  I run AMD64 (so no w32codecs  said:**
> 
I didn't know that.

[QUOTE=RAOF]
In short:  GStreamer 0.10 does not yet have a DVD-nav type element.  So, totem-gstreamer is not going to play your DVDs well.
I think there was some talk about gstreamer development post-Dapper release making it into Dapper via the updates repositories.  Just like the language packs.  I am not sure, though.

---

### Post by bsalt on 2006-07-05
does anyone know when Totem will officially support DVD playback - with the dvd nav features? i am waiting tooth and nail for it. and also, does anyone know when rhythmbox will support mtp devices?

---

