---
title: "Firefox Multimedia ?"
date: 2005-10-08
forum: Desktop Environments
---

### Post by mpierce on 2005-10-08
What plugins are required to play videos from within Firefox?

Here is an example:
[http://media.theage.com.au/?rid=16922&sy=age&source=theage.com.au%2Fsport%2Fmotorsport%2Findex.html](http://media.theage.com.au/?rid=16922&sy=age&source=theage.com.au%2Fsport%2Fmotorsport%2Findex.html)

---

### Post by Zelut on 2005-10-08
have you done the multimedia codecs from the [www.ubuntuguide.org?](www.ubuntuguide.org?)

---

### Post by mlomker on 2005-10-08
Mplayer can do it, assuming that you have the [w32codecs]("http://www.ubuntuforums.org/showpost.php?p=394904&postcount=18") already installed.  Add the **mozilla-mplayer** package (mplayer-i386 as well if you don't already have it installed).

---

### Post by mpierce on 2005-10-08
I have the codecs install and /usr/lib/win32 and have mplayer-586 and mplayer-plugin.
The problem is totem is trying to launch and I get the error Totem could not play 'fd://0' and I cannot uninstall totem as ubuntu desktop is dependant upon it.

---

### Post by mlomker on 2005-10-08
> ubuntu desktop is dependant upon it.

That's just a metapackage (a list of packages to install).  You can remove it.

---

### Post by weblars on 2005-10-08
You can remove the totem files from /usr/lib/mozilla-firefox/plugins. Just move every file containing libtotem to another directory.

---

### Post by SivArt on 2005-10-08
Hello, There's no plug-in for quick time or Wimdows Media Player for firefox using linux at this time,
but you can still use realplayer [http://www.real.com/R/RC.040104freeplayer.def...R/forms.real.com/real/player/unix/unix.html?rppr=rnwk&src=040104freeplayer]("http://www.real.com/R/RC.040104freeplayer.def...R/forms.real.com/real/player/unix/unix.html?rppr=rnwk&src=040104freeplayer")

You should use MozPlayerXP [http://mozplayerxp.mozdev.org/]("http://mozplayerxp.mozdev.org/")
Or the mplayer (but not tested) [http://mplayerplug-in.sourceforge.net/]("http://mplayerplug-in.sourceforge.net/")
This is the mozilla firefox plugin web page [https://pfs.mozilla.org/plugins/]("https://pfs.mozilla.org/plugins/")

Or you can acces this webpage for the complete list of plug-ins for firefox, mozilla and netscape [http://plugindoc.mozdev.org/linux.html]("http://plugindoc.mozdev.org/linux.html")


I hope you resolve your problem!!!:)

---

### Post by SivArt on 2005-10-08
[quote=SivArt]Hello, There's no plug-in for quick time or Wimdows Media Player for firefox using linux at this time,
but you can still use realplayer [http://www.real.com/R/RC.040104freeplayer.def...R/forms.real.com/real/player/unix/unix.html?rppr=rnwk&src=040104freeplayer]("http://www.real.com/R/RC.040104freeplayer.def...R/forms.real.com/real/player/unix/unix.html?rppr=rnwk&src=040104freeplayer")

You should use MozPlayerXP [http://mozplayerxp.mozdev.org/]("http://mozplayerxp.mozdev.org/")
Or the mplayer (but not tested) [http://mplayerplug-in.sourceforge.net/]("http://mplayerplug-in.sourceforge.net/")
This is the mozilla firefox plugin web page [https://pfs.mozilla.org/plugins/]("https://pfs.mozilla.org/plugins/")

Or you can acces this webpage for the complete list of plug-ins for firefox, mozilla and netscape [http://plugindoc.mozdev.org/linux.html]("http://plugindoc.mozdev.org/linux.html")


I hope you resolve your problem!!!:)[/quote]

You can also install xine plug-in [http://xinehq.de/index.php/releases]("http://xinehq.de/index.php/releases")

---

### Post by mpierce on 2005-10-08
I've moved the libtotem* plugins out of the way. No more error. 
I've linked the revelent mplayerplug-in.so & mplayerplug-in.xpt into /usr/lib/mozilla-firefox
I've cp the plugins for the plugin.tgz from mozdev.org into plugs.

I've still got nothing...
I cannot play the original file I referenced as a test or any other file.

Any other ideas?

---

### Post by weblars on 2005-10-09
You'd have to link the mplayer plugin files to /usr/lib/mozilla-firefox/plugins/. 
I'm running Breezy and can't test it now. But there should be an mplayer-mozilla package that installs all plugin files in the right directory.

Take a look at about : plugins. The mplayer plugin has to be listed there when it is installed properly.

---

### Post by mpierce on 2005-10-12
[QUOTE=weblars]You'd have to link the mplayer plugin files to /usr/lib/mozilla-firefox/plugins/. 
I'm running Breezy and can't test it now. But there should be an mplayer-mozilla package that installs all plugin files in the right directory.

Take a look at about : plugins. The mplayer plugin has to be listed there when it is installed properly.[/QUOTE]

Meant to say that!
Under about plugins, I only have application/x-mplayer2 listed.
What do I need?

---

### Post by weblars on 2005-10-12
With win32 codecs and mozilla-mplayer installed my about : config looks like

```

Google VLC multimedia plugin 1.0

    Dateiname: mplayerplug-in-gmp.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME-Typ 	Beschreibung 	Endungen 	Aktiviert
application/x-google-vlc-plugin 	Google Video 		Ja
QuickTime Plug-in 6.0

    Dateiname: mplayerplug-in-qt.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME-Typ 	Beschreibung 	Endungen 	Aktiviert
video/quicktime 	Quicktime 	mov 	Ja
video/x-quicktime 	Quicktime 	mov 	Ja
image/x-quicktime 	Quicktime 	mov 	Ja
video/quicktime 	Quicktime 	mp4 	Ja
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Ja
application/x-quicktimeplayer 	Quicktime 	mov 	Ja
application/smil 	SMIL 	smil 	Ja
RealPlayer 9

    Dateiname: mplayerplug-in-rm.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME-Typ 	Beschreibung 	Endungen 	Aktiviert
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Ja
audio/x-realaudio 	RealAudio 	ra 	Ja
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Ja
application/smil 	SMIL 	smil 	Ja
Windows Media Player Plugin

    Dateiname: mplayerplug-in-wmp.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME-Typ 	Beschreibung 	Endungen 	Aktiviert
application/asx 	Media Files 	* 	Ja
video/x-ms-asf-plugin 	Media Files 	* 	Ja
video/x-msvideo 	AVI 	avi,* 	Ja
video/msvideo 	AVI 	avi,* 	Ja
application/x-mplayer2 	Media Files 	* 	Ja
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Ja
video/x-ms-asf 	Media Files 	asf,asx,* 	Ja
video/x-ms-wm 	Media Files 	wm,* 	Ja
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Ja
video/x-ms-wmp 	Windows Media 	wmp,* 	Ja
video/x-ms-wvx 	Windows Media 	wvx,* 	Ja
audio/x-ms-wax 	Windows Media 	wax,* 	Ja
audio/x-ms-wma 	Windows Media 	wma,* 	Ja
application/x-drm-v2 	Windows Media 	asx,* 	Ja
audio/wav 	Microsoft wave file 	wav,* 	Ja
audio/x-wav 	Microsoft wave file 	wav,* 	Ja
mplayerplug-in 3.05

    Dateiname: mplayerplug-in.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME-Typ 	Beschreibung 	Endungen 	Aktiviert
video/mpeg 	MPEG 	mpg,mpeg 	Ja
audio/mpeg 	MPEG 	mpg,mpeg 	Ja
video/x-mpeg 	MPEG 	mpg,mpeg 	Ja
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Ja
audio/mpeg 	MPEG 	mpg,mpeg 	Ja
audio/x-mpeg 	MPEG 	mpg,mpeg 	Ja
audio/mpeg2 	MPEG audio 	mp2 	Ja
audio/x-mpeg2 	MPEG audio 	mp2 	Ja
audio/mpeg3 	MPEG audio 	mp3 	Ja
audio/x-mpeg3 	MPEG audio 	mp3 	Ja
audio/mp3 	MPEG audio 	mp3 	Ja
video/mp4 	MPEG 4 Video 	mp4 	Ja
application/x-ogg 	Ogg Vorbis Media 	ogg 	Ja
audio/ogg 	Ogg Vorbis Audio 	ogg 	Ja
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Ja
video/fli 	FLI animation 	fli,flc 	Ja
video/x-fli 	FLI animation 	fli,flc 	Ja
video/vnd.vivo 	VivoActive 	viv,vivo 	Ja
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Ja

```

In /usr/lib/mozilla-firefox/plugins I have

```
flashplayer.xpt        mplayerplug-in-gmp.xpt  mplayerplug-in.so
libflashplayer.so      mplayerplug-in-qt.so    mplayerplug-in-wmp.so
libjavaplugin_oji.so   mplayerplug-in-qt.xpt   mplayerplug-in-wmp.xpt
libnpsoplugin.so       mplayerplug-in-rm.so    mplayerplug-in.xpt
mplayerplug-in-gmp.so  mplayerplug-in-rm.xpt

```

But again, I'm on Breezy right now. Maybe somebody who is running Hoary can help here.

---

