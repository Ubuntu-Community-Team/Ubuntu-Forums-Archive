---
title: "Some mp3's play but others do not"
date: 2005-07-18
forum: Desktop Environments
---

### Post by mingus on 2005-07-18
I'm stumped on this one . . .

Some of my mp3 audio files will play, but others do not.  Strange.

In rhythmbox, the file(s) are skipped until the next playable file.
In totem, the "no file" message is displayed
In beep, the file name is displayed but no play is started, and the app locks up

On this same box I have SuSE and Kubuntu installed; the files that will not play on Ubuntu play just fine on those distros.

Of course I've installed the gstreamer etc libs, or no mp3's would play at all.  The only other variable I can see is that Ubuntu uses gnome; other sound diff's from kubuntu???

Ideas?

Thx in advance!

---

### Post by mingus on 2005-07-21
the plot thickens . . .

I discovered that if I hover the cursor over any of the mp3 files inside Nautilus that are not being recognized in *any* of the installed audio players, the file plays!  

The system monitor indicates that a child process was being called by Nautilus called "mpg123".

This verifies it is *not* a problem with the files themselves.

Anyone with an idea what mpg123 is, and why it would play within Nautilus when totem, rhythmbox and the others will not?

---

