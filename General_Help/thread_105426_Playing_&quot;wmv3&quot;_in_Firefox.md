---
title: "Playing &quot;wmv3&quot; in Firefox"
date: 2005-12-18
forum: General Help
---

### Post by kwaanens on 2005-12-18
I thought I had all necessary plugins necessary, but obviously not. I did from terminal:

```
$ firefox http://www.break.com/articles/pianoballs.html
*** loading the extensions datasource
[00000304] main decoder error: no suitable decoder module for fourcc `WMV3'.
VLC probably does not support this sound or video format.
```

Sound, but no video. Grrr...

Any hints?

- ketil

---

### Post by REBELinBLUE on 2005-12-18
WMV3 is Windows Media 9 which can not currently be played on linux. The VC1 specifications have just been published so hopefully soon we will start seeing an open source implementation of the decoder but don't hold your breath.

[http://www.nanocrew.net/2005/09/01/compiling-vlc/](http://www.nanocrew.net/2005/09/01/compiling-vlc/) details how to compile WMV support into VLC but you need to be a member of the Society of Motion Picture and Television Engineers in order to download the vc1 stuff

Hopefully soon, I have several WMV3 files which I want to play :(

---

### Post by yanik on 2005-12-18
works just fine here with the mplayerplug-in.

---

### Post by kwaanens on 2005-12-18
How do I decide which plugins should be used for which media files?

And what's up with all the Firefox/Mozilla media plugins? Is there any that I can get rid of?

Plugins right now are:
    * Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
    * Shockwave Flash
    * VLC multimedia plugin
    * OpenOffice.org Plug-in
    * Totem Mozilla Plugin
    * Java(TM) Plug-in Blackdown-1.4.2-02
    * Google VLC multimedia plugin 1.0
    * QuickTime Plug-in 6.0
    * RealPlayer 9
    * Windows Media Player Plugin
    * mplayerplug-in 3.05
    * Adobe Reader 7.0

So, I have Realplayer/Helix, VLC, Totem, Google VLC (whatever that is), Quicktime, Realplayer 9, Windows Media Player (is this because WMP is installed in Wine?) and Mplayer.
This *really* can't be necessary?

- Ketil

---

### Post by yanik on 2005-12-18
remove VLC multimedia plugin.

should be in /usr/lib/mozilla-firefox/plugins/

---

### Post by kwaanens on 2005-12-20
the Totem-plugin regularly acts up as well.
Now when I renamed the totem stuff, Mplayer tries to play the file. It seems to start playing on the site in the first post, but just stops after repeating "you know" twice.

Grrr...

- Ketil

---

### Post by antidrugue on 2005-12-20
[quote=kwaanens]the Totem-plugin regularly acts up as well.
Now when I renamed the totem stuff, Mplayer tries to play the file. It seems to start playing on the site in the first post, but just stops after repeating "you know" twice.

Grrr...

- Ketil[/quote]

Totem plugin act up?

Then you need to clean up "/usr/lib/mozilla-firefox/plugins" of any totem trace... (make a backup of any deleted files).

Then Totem won't show up its face anymore.

---

### Post by kwaanens on 2005-12-20
Why is Totem used anyway? To me, it seems, that it sucks completely. Most of the time it won't play anything at all.

But players like Mplayer usually does the trick.

Sigh... I just wish we could settle on one player that does it all, and then people can choose their favourite player on top of that, if they know what they're doing.

- Ketil

---

### Post by antidrugue on 2005-12-20
[quote=kwaanens]Why is Totem used anyway? To me, it seems, that it sucks completely. Most of the time it won't play anything at all.
[/quote]

Yop, completely true. 

MPlayer-plugin does the trick.

---

