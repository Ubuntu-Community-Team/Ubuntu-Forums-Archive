---
title: "VLC - force subtitle font"
date: 2009-06-16
forum: General Help
---

### Post by 6205 on 2009-06-16
It is possible somehow to force VLC player to use specific subtitle fonts? Because he is ignoring my settings and is still using some default sans, very bold and wide :(

---

### Post by lovinglinux on 2009-06-16
You can set the subtitles in the "Subtitles & OSD" section of the preferences. Set the path to the font you want to use in the option "Font" of the "Display" options. You need to stop and restart the video to make effect.

I would recommend you to try [ smplayer](apt:smplayer) [apt-get]. It has an excellent subtitle support and several nice features. In my opinion, it is as good as VLC or even better, depending on what you need.

---

### Post by 6205 on 2009-06-16
I have already set my custom font(Arial), but VLC ignores my settings. That's why i was asking for forcing that font.

Basically i am fine with Totem Gstreamer with all plugins like ffmpeg, good, bad, ugly - but it doesn't support **A**dvanced **S**ub**S**tation Alpha subtitles.(A-S-S)

How about smplayer, does it supports ***/SSA subtitles ? Also i want something what will blend with GNOME, so KDE crystal icons are unacceptable.

---

### Post by lovinglinux on 2009-06-16
> **6205 said:**
> I have already set my custom font(Arial), but VLC ignores my settings. That's why i was asking for forcing that font.

Something is wrong. Maybe you could try another font.


> **6205 said:**
> How about smplayer, does it supports ***/SSA subtitles ? Also i want something what will blend with GNOME, so KDE crystal icons are unacceptable.

Yes, it supports SSA subtitles. There are also several GUI options, including GTK/Gnome icons (see attachment).

---

### Post by 6205 on 2009-06-16
mmmm...i give it a try :)

btw. whats new in mplayer development, because look like they are inactive quite some time. also mplayer-plugin is almost a year old..

only VLC and gsreamer plugins are in constant development

---

### Post by lovinglinux on 2009-06-16
> **6205 said:**
> mmmm...i give it a try :)

btw. whats new in mplayer development, because look like they are inactive quite some time. also mplayer-plugin is almost a year old..

only VLC and gsreamer plugins are in constant development


I use [gecko-mediaplayer](apt:gecko-mediaplayer) [apt-get] plugin, which is great imo.

---

### Post by andrew.46 on 2009-06-16
Hi 6205,

> **6205 said:**
> btw. whats new in mplayer development, because look like they are inactive quite some time.

MPlayer has been in constant development with changes and improvements committed *every* day. What you have perhaps been looking at is the so-called rc versions, the last of which came out in 2007. There is however a newer version available in the Karmic repository.

Andrew

---

