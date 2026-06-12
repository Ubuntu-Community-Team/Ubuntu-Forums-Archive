---
title: "Windows streamed media in Firefox?"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Edward The Bonobo on 2006-08-30
Can I play Windows streams in Firefox?

At the moment I'm using Totem, with the gstreamer-totem-firefox-plugin, and I have all the codecs I can think of - but it doesn't work.

Should I try Mplayer?  And will this be OK for Realmedia?  I'm a little reluctant to switch, because it took me a long time to get Realmedia to play in Firefox.

---

### Post by lynxus on 2006-08-30
the mplayer plugin should work?

If not , do a google search for mplayer firefox linux plugin ?
That seems to play most windows files happily ( Esp if you have installed stuff from automatix )

---

### Post by Edward The Bonobo on 2006-08-30
I've now tried installing mplayer and mplayer-mozilla.

Now I can't play either Real or Windows media.  The plugin opens on the Firefox page and it looks like it's running the stream OK...except that it doesn't play the video or audio.

I also tried totem-xine, but that only worked for realmedia, same as totem-gstreamer.

Any ideas?  Maybe I'm missing something to make mplayer work?

---

### Post by CatKiller on 2006-08-31
> **Edward The Bonobo said:**
> I've now tried installing mplayer and mplayer-mozilla...

...Any ideas?  Maybe I'm missing something to make mplayer work?
Mine works, but I can't remember if it did before I installed w32codecs. Try installing that. It's not in the repositories, but there's a HOWTO - probably on this site somewhere - that explains how to do it.

That should magically give mplayer, and the mozilla-mplayer plugin, the ability to play all sorts of files.

---

### Post by Edward The Bonobo on 2006-08-31
I already have w32codecs. :(

---

### Post by CatKiller on 2006-08-31
> **Edward The Bonobo said:**
> I already have w32codecs. :(I don't really know what else to suggest. Sorry. If ALSA or whatever weren't working, then you'd probably notice that other things didn't have sound, I'd imagine. You can configure the mplayer plugin by right-clicking when something's trying to play. There might be something in there that strikes you as amiss.

---

### Post by df3n5 on 2006-08-31
What i did was used bumps,
[http://www.ubuntuforums.org/forumdisplay.php?f=143]("http://www.ubuntuforums.org/forumdisplay.php?f=143")

It sorted all of my streaming problems out with w32 using mplayer. Hope that helps.

---

