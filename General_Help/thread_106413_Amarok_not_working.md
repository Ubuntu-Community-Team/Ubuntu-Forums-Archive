---
title: "Amarok not working"
date: 2005-12-20
forum: General Help
---

### Post by Disorder2 on 2005-12-20
I have a fresh install of kubuntu breezy here.
I changed nothing in the default setup.

Now Amarok says "The gst-engine claims it cannot play mp3 files".
When I click to play a file anyway it tells me "Could not determine type of stream".

So I went and installed the brand new amarok 1.3.7 with all the plugins/engines
To make it short - I cannot get it to wortk with any of them (well, I haven't tried ALL combinations maybe but most).
Neither gstreamer nor artsd nor XINE give any output. The error messages differ but no result anyway.

Anything missing in the default installation?

Oh - yes, my system sound works
And amarok works on the hoary I have on another partition, so the files are OK and the soundcard is as well.....

Any ideas?

Thanks :smile:

---

### Post by noigeaR on 2005-12-20
mp3 playback doesn't work out of the box because of licensing issues. what you need for mp3 playback in amarok is the package **gstreamer0.8-mad**.
alternatively you can install **gstreamer0.8-plugins**. that's a metapackage which will install all available plugins for gstreamer (the mad plugin for mp3 too).
both packages are in the universe repository, so you'll have to add that to your sources.list if you haven't already done so.

---

### Post by Disorder2 on 2005-12-20
I had the gstreamer plugins installed and it didn't work.

Just installed gstreamer0.8-mad - and YES. NOISE.

Thanks a **bunch**

---

### Post by claydoh on 2005-12-20
Actually, you may need to install [akode-mpeg]("http://packages.ubuntu.com/breezy/sound/akode-mpeg") for mp3 playback. This package is in Universe. It is needed for kde/arts, but  not necessarily for Gnome

You're [B]welcome!

[/B]

---

### Post by noigeaR on 2005-12-20
akode-mpeg isn't installed on my system and mp3 playback works perfectly nevertheless. since kubuntu defaults to gstreamer as playback and not arts, it's not really necessary to install mp3 support for arts with akode-mpeg.
in a default kubuntu install, the musicplayers like amarok or juk normaly use the gstreamer engine for playback and for mp3 support in gstreamer you need gstreamer0.8-mad.

personaly i consider arts to be one of the worst pieces of software to be part of kde and so i try to avoid it at all cost (using gstreamer whenever possible).

---

### Post by claydoh on 2005-12-20
Yes, gstreamer may work well for many, but as I had problems with streams, I switched to the arts engine which works great for me

Maybe it will work for others too

---

### Post by ace2005 on 2005-12-21
Use arts, you're in KDE after all

Install amarok-arts

Go into kcontrol and pick Alsa as the output hardware, thats the one that works the best for me but you might want to try some of the others. Make sure that "Auto-Suspend if idle after" is set to something like 1 second, so that if amarok stops playing other apps can use the sound system

Go into amarok and pick arts as the engine and that should do it

If not install amarok-xine, go into xine and pick arts as audio output, then go into amarok and pick xine as the engine and it'll work, You might need to have the win32 codecs installed.


Edit: argh crap!

> personaly i consider arts to be one of the worst pieces of software to be part of kde and so i try to avoid it at all cost (using gstreamer whenever possible).

Well just use xine, but i think you should try arts first, arts will mix the sound from different sources. Gstreamerr for me doesn't work that well, some MP3s don't play properly

Edit: 2: IF you use arts as sound output in xine or any other video apps, you may find that the audio is out of sync and that there is a delay, so using alsa directly in video apps is the best thing to do, but its fine for just audio like playing MP3s

---

### Post by Frazer on 2005-12-22
[QUOTE=ace2005]Use arts, you're in KDE after all

Install amarok-arts

Go into kcontrol and pick Alsa as the output hardware, thats the one that works the best for me but you might want to try some of the others. Make sure that "Auto-Suspend if idle after" is set to something like 1 second, so that if amarok stops playing other apps can use the sound system

y[/QUOTE]

whey Thanks :D this fixed mp3 for me

---

### Post by rama on 2006-01-03
I had the exact same problem. Following ace2005's instructions I managed to solve it. Just out of curiosity how did this happen?
One more thing. I couldnt find the "Auto-Suspend if idle after" setting.

---

### Post by ace2005 on 2006-01-04
Open kcontrol via Konsole or Alt + F2 (Run Dialogue)
Go into "Sound and Multimedia"
Then into "Sound System"

At the bottom is a check box for "Auto-Suspend if idle after" set it to something like 1 second, this will let any other program use the sound 1 second after arts has stopped so /dev/dsp can be accessed directly by stuff like games

---

### Post by rama on 2006-01-04
Thx! I feel like I m a bit blind! Still any idea why amarok presented this problem?

---

