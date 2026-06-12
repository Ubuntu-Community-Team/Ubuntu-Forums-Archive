---
title: "mozplugger won't display images in firefox"
date: 2006-09-21
forum: Desktop Environments
---

### Post by nab on 2006-09-21
Hi all,

I installed mozplugger via Synaptic.

Testing the plugin with [http://fredrik.hubbe.net/plugger/test.html]("http://fredrik.hubbe.net/plugger/test.html")

I have no problem with Video. 
In the Music section MIDI, MPEG-url, Soundtracker, PSID and YM won't work. 
In the Image section only MS Bitmap and PNG is working.
In the documents only word and excel are working.

Well, at the moment I really need to display tiff's (US patents :D ).

Googling I didn't find any solution.


My about:plugins looks like:
[HTML]Installierte Plugins
Erfahren Sie mehr über Browser-Plugins auf Netscape.com.
Hilfe zum Installieren von Plugins ist verfügbar auf plugindoc.mozdev.org.
Shockwave Flash

    Dateiname: /usr/lib/flashplugin-nonfree/libflashplayer.so
    Shockwave Flash 7.0 r68

MIME-Typ 	Beschreibung 	Endungen 	Aktiviert
application/x-shockwave-flash 	Shockwave Flash 	swf 	Ja
application/futuresplash 	FutureSplash Player 	spl 	Ja
VLC multimedia plugin

    Dateiname: /usr/lib/mozilla/plugins/libvlcplugin.so
    VLC multimedia plugin

    version 0.8.5 Janus
    VideoLAN WWW: http://www.videolan.org/

MIME-Typ 	Beschreibung 	Endungen 	Aktiviert
audio/mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Ja
audio/x-mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Ja
video/mpeg 	MPEG video 	mpg,mpeg,mpe 	Ja
video/x-mpeg 	MPEG video 	mpg,mpeg,mpe 	Ja
video/mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Ja
video/x-mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Ja
video/mpeg4 	MPEG-4 video 	mp4,mpg4 	Ja
audio/mpeg4 	MPEG-4 audio 	mp4,mpg4 	Ja
application/mpeg4-iod 	MPEG-4 video 	mp4,mpg4 	Ja
application/mpeg4-muxcodetable 	MPEG-4 video 	mp4,mpg4 	Ja
video/x-msvideo 	AVI video 	avi 	Ja
video/quicktime 	QuickTime video 	mov,qt 	Ja
application/x-ogg 	Ogg stream 	ogg 	Ja
application/ogg 	Ogg stream 	ogg 	Ja
application/x-vlc-plugin 	VLC plugin 		Ja
video/x-ms-asf-plugin 	Windows Media Video 	asf,asx 	Ja
video/x-ms-asf 	Windows Media Video 	asf,asx 	Ja
application/x-mplayer2 	Windows Media 		Ja
video/x-ms-wmv 	Windows Media 	wmv 	Ja
application/x-google-vlc-plugin 	Google VLC pluginaudio/wav 	:WAV audioaudio/x-wav::WAV audio: 	Ja
Google VLC multimedia plugin 1.0

    Dateiname: /usr/lib/mozilla/plugins/mplayerplug-in-gmp.so
    mplayerplug-in 3.17

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME-Typ 	Beschreibung 	Endungen 	Aktiviert
application/x-google-vlc-plugin 	Google Video 		Ja
QuickTime Plug-in 6.0

    Dateiname: /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
    mplayerplug-in 3.17

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

    Dateiname: /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
    mplayerplug-in 3.17

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME-Typ 	Beschreibung 	Endungen 	Aktiviert
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Ja
application/vnd.rn-realmedia 	RealMedia 	rm 	Ja
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Ja
video/vnd.rn-realvideo 	RealVideo 	rv 	Ja
audio/x-realaudio 	RealAudio 	ra 	Ja
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Ja
application/smil 	SMIL 	smil 	Ja
Windows Media Player Plugin

    Dateiname: /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
    mplayerplug-in 3.17

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
audio/x-ms-wmv 	Windows Media 	wmv,* 	Ja
video/x-ms-wmp 	Windows Media 	wmp,* 	Ja
video/x-ms-wvx 	Windows Media 	wvx,* 	Ja
audio/x-ms-wax 	Windows Media 	wax,* 	Ja
audio/x-ms-wma 	Windows Media 	wma,* 	Ja
application/x-drm-v2 	Windows Media 	asx,* 	Ja
audio/wav 	Microsoft wave file 	wav,* 	Ja
audio/x-wav 	Microsoft wave file 	wav,* 	Ja
mplayerplug-in 3.17

    Dateiname: /usr/lib/mozilla/plugins/mplayerplug-in.so
    mplayerplug-in 3.17

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
video/mp4 	MPEG 4 Video 	mp4 	Ja
audio/mpeg3 	MPEG audio 	mp3 	Ja
audio/x-mpeg3 	MPEG audio 	mp3 	Ja
audio/mp3 	MPEG audio 	mp3 	Ja
application/x-ogg 	Ogg Vorbis Media 	ogg 	Ja
audio/ogg 	Ogg Vorbis Audio 	ogg 	Ja
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Ja
video/fli 	FLI animation 	fli,flc 	Ja
video/x-fli 	FLI animation 	fli,flc 	Ja
video/vnd.vivo 	VivoActive 	viv,vivo 	Ja
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Ja
video/vnd.divx 	DivX Media Format 	divx 	Ja
audio/basic 	Basic Audio File 	au,snd 	Ja
audio/x-basic 	Basic Audio File 	au,snd 	Ja
Java(TM) Plug-in 1.5.0_06-b05

    Dateiname: /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_06

MIME-Typ 	Beschreibung 	Endungen 	Aktiviert
application/x-java-vm 	Java 		Ja
application/x-java-applet 	Java 		Ja
application/x-java-applet;version=1.1 	Java 		Ja
application/x-java-applet;version=1.1.1 	Java 		Ja
application/x-java-applet;version=1.1.2 	Java 		Ja
application/x-java-applet;version=1.1.3 	Java 		Ja
application/x-java-applet;version=1.2 	Java 		Ja
application/x-java-applet;version=1.2.1 	Java 		Ja
application/x-java-applet;version=1.2.2 	Java 		Ja
application/x-java-applet;version=1.3 	Java 		Ja
application/x-java-applet;version=1.3.1 	Java 		Ja
application/x-java-applet;version=1.4 	Java 		Ja
application/x-java-applet;version=1.4.1 	Java 		Ja
application/x-java-applet;version=1.4.2 	Java 		Ja
application/x-java-applet;version=1.5 	Java 		Ja
application/x-java-applet;jpi-version=1.5.0_06 	Java 		Ja
application/x-java-bean 	Java 		Ja
application/x-java-bean;version=1.1 	Java 		Ja
application/x-java-bean;version=1.1.1 	Java 		Ja
application/x-java-bean;version=1.1.2 	Java 		Ja
application/x-java-bean;version=1.1.3 	Java 		Ja
application/x-java-bean;version=1.2 	Java 		Ja
application/x-java-bean;version=1.2.1 	Java 		Ja
application/x-java-bean;version=1.2.2 	Java 		Ja
application/x-java-bean;version=1.3 	Java 		Ja
application/x-java-bean;version=1.3.1 	Java 		Ja
application/x-java-bean;version=1.4 	Java 		Ja
application/x-java-bean;version=1.4.1 	Java 		Ja
application/x-java-bean;version=1.4.2 	Java 		Ja
application/x-java-bean;version=1.5 	Java 		Ja
application/x-java-bean;jpi-version=1.5.0_06 	Java 		Ja
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    Dateiname: /usr/lib/mozilla/plugins/nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.572 built with gcc 3.2.0 on Sep 15 2005

MIME-Typ 	Beschreibung 	Endungen 	Aktiviert
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Ja
MozPlugger 1.7.1

    Dateiname: /usr/lib/mozilla/plugins/mozplugger.so
    MozPlugger version 1.7.1, written by Fredrik Hübinette <hubbe@hubbe.net> and Louis Bavoil <louis@bavoil.net>.
    For documentation on how to configure mozplugger, check the man page. (type man mozplugger)
    Configuration file:	/etc/mozpluggerrc
    Helper binary:	mozplugger-helper
    Controller binary:	mozplugger-controller

MIME-Typ 	Beschreibung 	Endungen 	Aktiviert
video/mpeg 	MPEG animation 	mpeg, mpg, mpe 	Ja
video/x-mpeg 	MPEG animation 	mpeg, mpg, mpe 	Ja
video/x-mpeg2 	MPEG2 animation 	mpv2, mp2ve 	Ja
video/mp4 	MPEG4 animation 	mp4 	Ja
video/msvideo 	AVI animation 	avi 	Ja
video/x-msvideo 	AVI animation 	avi 	Ja
video/fli 	FLI animation 	fli, flc 	Ja
video/x-fli 	FLI animation 	fli, flc 	Ja
application/x-mplayer2 	Windows Media 	wmv,asf,mov 	Ja
video/x-ms-asf 	Windows Media 	asf,asx,wma,wax,wmv,wvx 	Ja
video/x-ms-wmv 	Windows Media 	wmv 	Ja
application/x-quicktimeplayer 	Quicktime animation 	mov 	Ja
image/x-macpaint 	Quicktime animation 	pntg,mov 	Ja
video/quicktime 	Quicktime animation 	mov,qt 	Ja
video/x-quicktime 	Quicktime animation 	mov,qt 	Ja
video/x-theora 	OGG stream with video 	ogg 	Ja
video/theora 	OGG stream with video 	ogg 	Ja
video/ogg 	OGG stream with video 	ogg 	Ja
video/x-ogg 	OGG stream with video 	ogm,ogv 	Ja
audio/mid 	MIDI audio file 	midi,mid 	Ja
audio/x-mid 	MIDI audio file 	midi,mid 	Ja
audio/midi 	MIDI audio file 	midi,mid 	Ja
audio/x-midi 	MIDI audio file 	midi,mid 	Ja
audio/mp3 	MPEG audio 	mp3 	Ja
audio/x-mp3 	MPEG audio 	mp3 	Ja
audio/mpeg2 	MPEG audio 	mp2 	Ja
audio/x-mpeg2 	MPEG audio 	mp2 	Ja
audio/mpeg3 	MPEG audio 	mp3 	Ja
audio/x-mpeg3 	MPEG audio 	mp3 	Ja
audio/mpeg 	MPEG audio 	mpa,abs,mpega 	Ja
audio/x-mpeg 	MPEG audio 	mpa,abs,mpega 	Ja
audio/x-ogg 	OGG audio 	ogg 	Ja
application/x-ogg 	OGG audio 	ogg 	Ja
application/ogg 	OGG audio 	ogg 	Ja
audio/basic 	Basic audio file 	au,snd 	Ja
audio/x-basic 	Basic audio file 	au,snd 	Ja
audio/wav 	Microsoft wave file 	wav 	Ja
audio/x-wav 	Microsoft wave file 	wav 	Ja
audio/x-pn-wav 	Microsoft wave file 	wav 	Ja
audio/x-pn-windows-acm 	Microsoft wave file 	wav 	Ja
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Ja
audio/x-pn-realaudio 	Realaudio-plugin resource locator 	ra,rm,ram 	Ja
audio/x-realaudio 	RealAudio file 	ra,rm,ram 	Ja
application/vnd.rn-realmedia 	RealMedia file 	rm 	Ja
application/smil 	RealPlayer 	smi 	Ja
audio/vnd.rn-realaudio 	RealAudio file 	ra,ram 	Ja
audio/vnd.rn-realvideo 	RealVideo file 	rv 	Ja
audio/x-ms-wax 	Windows Media 	wax,wma 	Ja
application/pdf 	PDF file 	pdf 	Ja
application/x-pdf 	PDF file 	pdf 	Ja
text/pdf 	PDF file 	pdf 	Ja
text/x-pdf 	PDF file 	pdf 	Ja
application/x-rtf 	Rich Text Format 	rtf 	Ja
application/rtf 	Rich Text Format 	rtf 	Ja
text/rtf 	Rich Text Format 	rtf 	Ja
application/x-msword 	Microsoft Word Document 	doc, dot 	Ja
application/msword 	Microsoft Word Document 	doc, dot 	Ja
application/vnd.ms-excel 	Microsoft Excel Document 	xls, xlb 	Ja
application/vnd.sun.xml.writer 	OpenOffice Writer 6.0 documents 	sxw 	Ja
application/so7_vnd.sun.xml.writer 	OpenOffice Writer 7.0 documents 	sxw 	Ja
application/vnd.sun.xml.writer.template 	OpenOffice Writer 6.0 templates 	stw 	Ja
application/vnd.sun.xml.writer.global 	OpenOffice Writer 6.0 global documents 	sxg 	Ja
application/vnd.stardivision.writer 	StarWriter 5.x documents 	sdw 	Ja
application/vnd.stardivision.writer-global 	StarWriter 5.x global documents 	sgl 	Ja
application/x-starwriter 	StarWriter 4.x documents 	sdw 	Ja
application/vnd.sun.xml.calc 	OpenOffice Calc 6.0 spreadsheets 	sxc 	Ja
application/so7_vnd.sun.xml.calc 	OpenOffice Calc 7.0 spreadsheets 	sxc 	Ja
application/vnd.sun.xml.calc.template 	OpenOffice Calc 6.0 templates 	stc 	Ja
application/vnd.stardivision.calc 	StarCalc 5.x spreadsheets 	sdc 	Ja
application/x-starcalc 	StarCalc 4.x spreadsheets 	sdc 	Ja
application/vnd.sun.xml.draw 	OpenOffice Draw 6.0 documents 	sxd 	Ja
application/so7_vnd.sun.xml.draw 	StarOffice Draw 7.0 documents 	sxc 	Ja
application/vnd.sun.xml.draw.template 	OpenOffice Draw 6.0 templates 	std 	Ja
application/vnd.stardivision.draw 	StarDraw 5.x documents 	sda 	Ja
application/x-stardraw 	StarDraw 4.x documents 	sda 	Ja
application/vnd.sun.xml.impress 	OpenOffice Impress 6.0 presentations 	sxi 	Ja
application/so7_vnd.sun.xml.impress 	StarOffice 7.0 Impress presentations 	sxi 	Ja
application/vnd.sun.xml.impress.template 	OpenOffice Impress 6.0 templates 	sti 	Ja
application/vnd.stardivision.impress 	StarImpress 5.x presentations 	sdd 	Ja
application/vnd.stardivision.impress-packed 	StarImpress Packed 5.x files 	sdp 	Ja
application/x-starimpress 	StarImpress 4.x presentations 	sdd 	Ja
application/vnd.ms-powerpoint 	PowerPoint Slideshow 	ppt 	Ja
application/mspowerpoint 	PowerPoint Slideshow 	ppt, ppz, pps, pot 	Ja
application/vnd.sun.xml.math 	OpenOffice Math 6.0 documents 	sxm 	Ja
application/so7_vnd.sun.xml.math 	StarOffice 7.0 Math documents 	sxm 	Ja
application/vnd.stardivision.math 	StarMath 5.x documents 	smf 	Ja
application/x-starmath 	StarMath 4.x documents 	smf 	Ja
[/HTML]

As I understand this list the images aren't linked to mozplugger. Can anybody forward me in the right direction, how I can add the mime types in firefox and mozplugger?

Thank you in advance,
Niko

---

### Post by nab on 2006-09-23
Hi,

I found out, how to display tifs :-)

I added in the tiff-section in etc/mozpluggerrc:
repeat noisy swallow(eog) fill: eog "$file"

So it seems that mozplugger just uses some programs I hadn't installed :p 

Niko

---

