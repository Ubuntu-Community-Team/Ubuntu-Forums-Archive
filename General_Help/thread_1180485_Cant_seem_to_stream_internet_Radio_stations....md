---
title: "Cant seem to stream internet Radio stations..."
date: 2009-06-06
forum: General Help
---

### Post by sports fan Matt on 2009-06-06
Hello all,
Im having a hell of a time trying to get anything from clear channel (as a web stream) to work with Opera.  It loads then it immediately shuts down..Any ideas?

Running  Version
10.00 Beta
Build
4402
Platform
Linux
System
i686, 2.6.28-12-generic
Qt library
3.3.8b
Java
Java Runtime Environment installed
Browser identification

Here is my plugins pathPlug-in path
/usr/lib/opera/plugins
/usr/lib/mozilla/plugins:

---

### Post by jonobr on 2009-06-06
Have your tried using firefox/swiftweasel or seamonkey to rule out browser issues?

Have  you tried other radio stations that present in different format?

I do a lot of streaming of local radio stations in the bay area on 9.04 and 8.10 through the above browsers with no major problems?
If all the above doesnt work, are you using a WISP?

You mention clear channel, Im not sure what they provide in your area, 
but some wireless providors who offer EVDO, Wireless 3G, EDGE and other wireless technologies can be a bit touchy about people stayin g online and streaming for extended periods.
I know the fine print of Verizon wireless EVDO service when I had it said they could cut you off immediately for doing security camera streaming and things like sling box.

---

### Post by sports fan Matt on 2009-06-07
Seems at least to me garbled in FF as well..Here is the website : [http://www.959theranch.com/](http://www.959theranch.com/)

It seems garbled and not wanting to play in either browser...

---

### Post by sports fan Matt on 2009-06-07
it sped up for me really fast then shut down after about 5 seconds..same in opera...Im using the mplayer plugin..

---

### Post by zika on 2009-06-07
> **sox fan Matt said:**
> Seems at least to me garbled in FF as well..Here is the website : [http://www.959theranch.com/](http://www.959theranch.com/)

It seems garbled and not wanting to play in either browser...
I listen streams whole day and this one is unusable here also. It seems it is not Your setup at fault.

---

### Post by sports fan Matt on 2009-06-07
Im glad to hear this...thought it was my fault.

---

### Post by jonobr on 2009-06-07
Agreed


Not your setup I think.

---

### Post by Soul-Sing on 2009-06-07
Why not using streaming audio with rhytmbox?
9.04

```
gedit ~/.local/share/rhythmbox/rhythmdb.xml
```

8.04.2

```
gedit ~/.gnome2/rhythmbox/rhythmdb.xml
```

Copy within gedit before "</rhythmdb>" your streaming "string"preferences.

example (dutch situation): 

<entry type="iradio">
<title>Radio 538</title> <genre>Pop</genre> <artist/>     
<album/> <location>[COLOR="Red"]http://www.radiodigitaal.nl/asx/radio538/538stream.asx</location>[/COLOR] <play-count>3</play-count> <last-played>1237571040</last-played> <date>0</date> <mimetype>application/octet-stream</mimetype> <mb-trackid/> <mb-artistid/> <mb-albumid/> <mb-albumartistid/> <mb-artistsortname/>

---

### Post by sports fan Matt on 2009-06-09
that station works but not in the latest opera 10: here is my windows media player plugin list: Windows Media Player Plug-inaudio/wav	wav
audio/x-wav	wav
video/x-msvideo	avi,asf,wmv
application/asx	asx
video/x-ms-asf-plugin	asf,wmv,asx
application/x-mplayer2	avi,wma,wmv
video/x-ms-wm	wm,wmv
audio/x-ms-wma	wma
audio/x-ms-wax	wax
video/x-ms-wvx	wvx,wmv
video/x-ms-wmv	wmv,wmx
video/x-ms-asf	asf,asx
video/x-ms-wmp	wmv,wmp
application/x-ms-wmp	wmp
video/msvideo	avi
application/x-ms-wmv	wmv
audio/x-ms-wmv	wmv
application/x-drm-v2	asx
/usr/lib/mozilla/plugins/gecko-mediaplayer-wmp.so

Windows Media Player Plug-inaudio/wav	wav
audio/x-wav	wav
video/x-msvideo	avi,asf,wmv
application/asx	asx
video/x-ms-asf-plugin	asf,wmv,asx
application/x-mplayer2	avi,wma,wmv
video/x-ms-wm	wm,wmv
audio/x-ms-wma	wma
audio/x-ms-wax	wax
video/x-ms-wvx	wvx,wmv
video/x-ms-wmv	wmv,wmx
video/x-ms-asf	asf,asx
video/x-ms-wmp	wmv,wmp
application/x-ms-wmp	wmp
video/msvideo	avi
application/x-ms-wmv	wmv
audio/x-ms-wmv	wmv
application/x-drm-v2	asx
/usr/lib/mozilla/plugins/mplayerplug-in-wmp.so

@leo..Ive never tried rhythymbox...

---

