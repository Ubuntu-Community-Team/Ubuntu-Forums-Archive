---
title: "Problems reading Adobe pdf files with either SeaMonkey or Firefox"
date: 2010-04-18
forum: Desktop Environments
---

### Post by fritzman on 2010-04-18
My OS is Ubuntu 9.04, and I have both SeaMonkey and Firefox installed, as well as Internet Explorer 6, using Wine, installed.  (Note the attached screenshot of the SeaMonkey Plugins.)
Adobe Reader 9.3

    File name: npwrapper.nppdf.so
    The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser. 

MIME Type 	Description 	Suffixes 	Enabled
application/pdf 	Portable Document Format 	pdf 	Yes
application/vnd.fdf 	Acrobat Forms Data Format 	fdf 	Yes
application/vnd.adobe.xfdf 	XML Version of Acrobat Forms Data Format 	xfdf 	Yes
application/vnd.adobe.xdp+xml 	Acrobat XML Data Package 	xdp 	Yes
application/vnd.adobe.xfd+xml 	Adobe FormFlow99 Data File 	xfd 	Yes
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r45

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
VLC Multimedia Plugin (compatible Totem 2.26.1)

    File name: libtotem-cone-plugin.so
    The Totem 2.26.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-vlc-plugin 	VLC Multimedia Plugin 		Yes
application/vlc 	VLC Multimedia Plugin 		Yes
video/x-google-vlc-plugin 	VLC Multimedia Plugin 		Yes
application/x-ogg 	Ogg multimedia file 	ogg 	Yes
application/ogg 	Ogg multimedia file 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	Annodex exchange format 	anx 	Yes
audio/annodex 	Annodex Audio 	axa 	Yes
video/annodex 	Annodex Video 	axv 	Yes
video/mpeg 	Movie Clip 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
application/x-totem-plugin 	Totem Multimedia plugin 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.26.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Windows Media video 	wmv 	Yes
video/x-ms-wm 	Windows Media video 	wmv 	Yes
video/x-ms-wmp 	Windows Media video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/x-ms-wmp 	Windows Media video 	wmp 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.26.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes

I'm experiencing a problem with both Firefox and SeaMonkey opening online pdf documents.  (Note the attached screenshot.) file:///home/al/iexplore-mozilla/MHDataXfer.pdf-page.png


As we can see, the page is blank.  If I copy the page to a folder on my computer, I can then open the invisible pdf file using Adobe Reader 9, and it is perfectly readable and can be printed.

If I use Internet Explorer 6, I can navigate to the same page, and open the same pdf file online, and it is perfectly readable online in an Adobe pdf format, and can be printed directly from that page.  
I've been dinking around with this problem for some time.  Although I can use the work-around mentioned, saving the page to my computer, and opening it separately with Adobe, this is really annoying.
This does not happen on all sites.  In fact, on most sites Adobe reader works just fine.  The maintainer of the site, not surprisingly, suggests that I use Internet Explorer, as that is the browser which they support.

Any clues?
Thanks, owa:confused:

---

### Post by lovinglinux on 2010-04-18
Do you have a special reason to use Adobe PDF reader instead of an open source alternative?

Even when I was a clueless Windows user I didn't use it. It sucks really bad. Have you tried [Evince](apt:evince)? I use Okular (I'm on KDE) and it works great, although for on-line viewing I have solved all my problems with [gPDF](https://addons.mozilla.org/en-US/firefox/addon/14814). It scan webpages for pdf links and set them to open with Google PDF viewer. Works like a charm.

---

