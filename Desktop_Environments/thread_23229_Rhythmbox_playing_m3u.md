---
title: "Rhythmbox playing m3u"
date: 2005-03-31
forum: Desktop Environments
---

### Post by imc on 2005-03-31
First thing I did when I got my install fired up(newbite), was try to load up streaming audio from protonradio.com.

I got this error message:
*There is no element present to handle the stream's mime type audio/mpeg.* 

Any ideas why I'm getting this?  XMMS on my SuSE install, and obviously i-tunes on windows has no issues playing streaming audio.  Doing some google searches only mentioned the problem, but no fixes.  Help?

---

### Post by André on 2005-04-01
Hi,

i think the problem is that the stream has an unsupported format.

Instead of using Google you could do a search in the forum:

[http://ubuntuforums.org/showthread.php?t=16526&highlight=rhythmbox+stream](http://ubuntuforums.org/showthread.php?t=16526&highlight=rhythmbox+stream)

[http://ubuntuforums.org/showthread.php?t=22313&highlight=rhythmbox+stream](http://ubuntuforums.org/showthread.php?t=22313&highlight=rhythmbox+stream)

Anyways the solution will hopefully be to install the gstreamer-plugins.

Note: There are several plugins for gstreamer but one is a metapackage to get them all. Install this one, for example via synaptic or :

"Enable the universe repository and sudo apt-get update and sudo apt-get install gstreamer-plugins."

I hope this helps.

André

P.S.: AFAIK m3u is the appendix for playlists and not for streams? That makes your title some kind of misleading ;-)

---

### Post by SFN on 2005-04-08
[QUOTE=André]P.S.: AFAIK m3u is the appendix for playlists and not for streams? That makes your title some kind of misleading ;-)[/QUOTE]

The links for mount points of OGG streams through Icecast (and possibly others but Icecast OGG's for sure) have an m3u appended to the end of them. As in "stream.ogg.m3u".

---

### Post by gvangelder on 2005-04-11
Since I found this thread as the first hit through google, I just want to point out that the previous poster was right and to be able to play internet radio stations such as digitally imported and club 977 in rhythmbox, you need to install the gstreamer plugins and you'll be good to go.

Though the real package name i needed to use was gstreamer0.8-plugins

Thanks ubuntu for a great distro!

---

