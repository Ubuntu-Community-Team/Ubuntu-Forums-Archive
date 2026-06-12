---
title: "Has anyone gotten totem-xine-firefox-plugin + w32codecs to play wmv files?"
date: 2005-12-13
forum: General Help
---

### Post by brynjarh on 2005-12-13
Has anyone gotten the totem-xine-firefox-plugin to play embeded wmv files? I haven't tried any other type of file but when I play an embeded wmv file like for example this one here [http://hugi.is/hahradi/bigboxes.php?box_id=51208&f_id=1487]("http://hugi.is/hahradi/bigboxes.php?box_id=51208&f_id=1487") it starts playing but then stops, and all I see is a static image of the beginning of the file, the system is stable, nothing else changes.

Now when I run totem and tell it to open the file directly, Ctrl+L or Movie > Open Location... [http://media.hugi.is/hahradi/fyndnar/2005_gemenos_castellana.wmv]("http://media.hugi.is/hahradi/fyndnar/2005_gemenos_castellana.wmv") it plays just fine.

So I guess this is a problem with the plugin, is this a known problem? Are there any workarounds?

And to complicate this thread a bit, does there exist a wmv9 plugin for gstreamer for Ubuntu? If so, where could one find a .deb or a repository for that? I personally like gstreamer better then xine though it has never been able to play more then 1% of my video files, I'm hoping that *some day* I can replace xine with gstreamer.

I'm using Totem 1.2.1 from breezy-backports and w32codecs made for Ubuntu, more about that at [http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu]("http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu"), I am pretty sure that this problem also occurs on Totem 1.2.0.

---

### Post by Corvillus on 2005-12-13
I could never get the totem plugin working. What I ended up doing was instead installing the MPlayer plugin, then moving all the totem plugins to a different directory to force Firefox to use the MPlayer one instead.

You can do this by enabling the universe and multiverse repositories, then

```
sudo apt-get install mozilla-mplayer
cd /usr/lib/mozilla-firefox/plugins
sudo mkdir totemplugins
sudo mv libtotem_mozilla.* totemplugins
```

After doing that, restart Firefox and you should be able to play most web video content fine.

---

### Post by 0okami on 2005-12-13
[QUOTE=Corvillus]I could never get the totem plugin working. What I ended up doing was instead installing the MPlayer plugin, then moving all the totem plugins to a different directory to force Firefox to use the MPlayer one instead.
[/QUOTE]

mplayer plugins working just fine here. :) never tried totem plugins... i read they are a headache sometimes at the moment..

---

### Post by brynjarh on 2005-12-13
Yeah I've heard great things about mplayer from people who want things to work **right now** so if I would be interested in that I would definitely go with mplayer.

My interest lies with the future which my instinct and knowledge tells me is gstreamer but I'm also interested in balancing the future and **right now** so xine is my choice for that balance because..

1.Xine works with Totem which is default for GNOME and looks promising.
2.Totem has a firefox(epiphany/mozilla) plugin which I expect to be **stable** in Ubuntu 6.04.
3.Xine works with codecs created for mplayer.
4.It's easy to switch between xine and gstreamer in Totem, this will come in handy when gstreamer is ready.
5.Xine + mplayer codecs can play what I need, though not in embedded web pages **right now**.

So it's a good balance between now and later since embedded web video playing is not something I need desperately to survive or be happy. :D

Just wondering if someone clever had gotten totem+xine+w32codecs+firefox-plugin to work for wmv on Ubuntu 5.10.

---

