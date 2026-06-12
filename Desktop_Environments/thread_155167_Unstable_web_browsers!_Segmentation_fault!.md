---
title: "Unstable web browsers! Segmentation fault!"
date: 2006-04-04
forum: Desktop Environments
---

### Post by Biffy on 2006-04-04
For a time back, i was using Opera and had a problem with it. Sometimes (not all the time) when i clicked on a link or the browser was loading heavy, it would just shut down. This was of course annoying so i started Opera from a terminal and when it crashed, it just posted the message "segmentation fault". This problem could happen from once each day to once in a couple of days. It crashed a lot, that is. I posted some in the Opera forums, trying a lot of stuff, including the static version, but nothing helped.

So i began using firefox instead. It didnt crash for five days, so i tought it was stable. ..Until it also crashed exactly the same way as Opera crashed. When clicking on a link, the webbrowser just shuts down. For example, it crashed five minutes ago when clicking an e-mail link on a regular, simple web page. I clicked on it now again, and it doesent crash. So this just happens randomly and a link that crashed the browser the other day can work fine afterwards. And i repeat myself, the browser could also crash when it is loading a page. But mostly is crashes when clicking a link. The link issue has been the only thing that's been crashing firefox.

So, i ran firefox via a terminal and here is the error message after it had crashed:

```
larsson@ubuntu:~/Downloads/firefox $ ./firefox
./run-mozilla.sh: line 131: 22498 Segmentation fault      "$prog" ${1+"$@"}
```

I've been using the latest version of Firefox but the one in the reps are also crashing. 

Theese are the plugins im using:
Flash *(Dont know about this one, been upgrading to new version and it didnt help)*
Java
Mplayer-plugin *(i know this plugin isnt causing it cause i installed it after the first crash and besides, Opera doesent have it enabled)*

When typing "about:plugins" , this is what i get:

```
Google VLC multimedia plugin 1.0

    File name: mplayerplug-in-gmp.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/x-google-vlc-plugin 	Google Video 		Yes
QuickTime Plug-in 6.0

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
application/smil 	SMIL 	smil 	Yes
RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes
Windows Media Player Plugin

    File name: mplayerplug-in-wmp.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/asx 	Media Files 	* 	Yes
video/x-ms-asf-plugin 	Media Files 	* 	Yes
video/x-msvideo 	AVI 	avi,* 	Yes
video/msvideo 	AVI 	avi,* 	Yes
application/x-mplayer2 	Media Files 	* 	Yes
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-asf 	Media Files 	asf,asx,* 	Yes
video/x-ms-wm 	Media Files 	wm,* 	Yes
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-wmp 	Windows Media 	wmp,* 	Yes
video/x-ms-wvx 	Windows Media 	wvx,* 	Yes
audio/x-ms-wax 	Windows Media 	wax,* 	Yes
audio/x-ms-wma 	Windows Media 	wma,* 	Yes
application/x-drm-v2 	Windows Media 	asx,* 	Yes
audio/wav 	Microsoft wave file 	wav,* 	Yes
audio/x-wav 	Microsoft wave file 	wav,* 	Yes
mplayerplug-in 3.05

    File name: mplayerplug-in.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r63

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Java(TM) Plug-in 1.5.0_01-b08

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_01

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;jpi-version=1.5.0_01 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;jpi-version=1.5.0_01 	Java
```

Unstable webbrowsers are very annoying, and no fun at all to use. Please help me with this!

---

### Post by Gautam Arjun on 2006-04-05
Hi,
     Firefox 1.5 crashes with the exact same message for me as well - but when I visit quicktime-embedded pages ( not random crashes). I just switched to using Epiphany.

---

### Post by Biffy on 2006-04-05
Well, i have this problem on both Firefox and Opera so a switch to another browser probably wont fix it.

---

### Post by mambru on 2006-04-05
I'm afraid the problem is ubuntu. I used the latest firefox, opera, mozilla and seamonkey versions on debian sarge and never had such a problem like this. Since I've changed from debian to ubuntu (about a week) firefox have crashed three times with the "segmentation fault" message and the only solution I've figured out, has been to re-install it all over. It's been three times, so far . If anybody knows a way to solve this problem, please, let us know it. That'd be great.

---

### Post by Biffy on 2006-04-05
Very nice to hear that im not the only one with this problem. 

Well, if the problem lies withing Ubuntu, maybe this will be solved in Dapper that is being released in a couple of months?

---

### Post by blknit on 2006-04-18
[QUOTE=Biffy]For a time back, i was using Opera and had a problem with it. Sometimes (not all the time) when i clicked on a link or the browser was loading heavy, it would just shut down. This was of course annoying so i started Opera from a terminal and when it crashed, it just posted the message "segmentation fault". This problem could happen from once each day to once in a couple of days. It crashed a lot, that is. I posted some in the Opera forums, trying a lot of stuff, including the static version, but nothing helped.

So i began using firefox instead. It didnt crash for five days, so i tought it was stable. ..Until it also crashed exactly the same way as Opera crashed. When clicking on a link, the webbrowser just shuts down. For example, it crashed five minutes ago when clicking an e-mail link on a regular, simple web page. I clicked on it now again, and it doesent crash. So this just happens randomly and a link that crashed the browser the other day can work fine afterwards. And i repeat myself, the browser could also crash when it is loading a page. But mostly is crashes when clicking a link. The link issue has been the only thing that's been crashing firefox.

So, i ran firefox via a terminal and here is the error message after it had crashed:

```
larsson@ubuntu:~/Downloads/firefox $ ./firefox
./run-mozilla.sh: line 131: 22498 Segmentation fault      "$prog" ${1+"$@"}
```

I've been using the latest version of Firefox but the one in the reps are also crashing. 

Theese are the plugins im using:
Flash *(Dont know about this one, been upgrading to new version and it didnt help)*
Java
Mplayer-plugin *(i know this plugin isnt causing it cause i installed it after the first crash and besides, Opera doesent have it enabled)*

When typing "about:plugins" , this is what i get:

```
Google VLC multimedia plugin 1.0

    File name: mplayerplug-in-gmp.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/x-google-vlc-plugin 	Google Video 		Yes
QuickTime Plug-in 6.0

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
application/smil 	SMIL 	smil 	Yes
RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes
Windows Media Player Plugin

    File name: mplayerplug-in-wmp.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/asx 	Media Files 	* 	Yes
video/x-ms-asf-plugin 	Media Files 	* 	Yes
video/x-msvideo 	AVI 	avi,* 	Yes
video/msvideo 	AVI 	avi,* 	Yes
application/x-mplayer2 	Media Files 	* 	Yes
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-asf 	Media Files 	asf,asx,* 	Yes
video/x-ms-wm 	Media Files 	wm,* 	Yes
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-wmp 	Windows Media 	wmp,* 	Yes
video/x-ms-wvx 	Windows Media 	wvx,* 	Yes
audio/x-ms-wax 	Windows Media 	wax,* 	Yes
audio/x-ms-wma 	Windows Media 	wma,* 	Yes
application/x-drm-v2 	Windows Media 	asx,* 	Yes
audio/wav 	Microsoft wave file 	wav,* 	Yes
audio/x-wav 	Microsoft wave file 	wav,* 	Yes
mplayerplug-in 3.05

    File name: mplayerplug-in.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r63

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Java(TM) Plug-in 1.5.0_01-b08

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_01

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;jpi-version=1.5.0_01 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;jpi-version=1.5.0_01 	Java
```

Unstable webbrowsers are very annoying, and no fun at all to use. Please help me with this![/QUOTE]

I resolved the Opera problem installing the "Other/Static deb" version downloaded from Opera web site.

Hope it helps

---

### Post by Biffy on 2006-04-18
> I posted some in the Opera forums, trying a lot of stuff, **including the static version**, but nothing helped.


:)

---

### Post by RavenOfOdin on 2006-05-01
I haven't had one single problem with Konqueror, yet.
Except sometimes I have to switch to Epiphany to download material from a particular page.

Firefox can also crash when you overload it with too many extensions. That's happened to me both on XP and Ubuntu.

As for Opera, I never liked its running memory usage total. . .so. . .meh. :p

---

### Post by TimelessRogue on 2006-05-01
I've been experiencing this 'instability' problem with Firefox in both Windoze 2k and Ubuntu Breezy for some time now ... and it's not due to the use of Quicktime since I haven't used it or other video schemes.  Even without extensions loaded it crashes.

I've used Opera in both OS' ... generally with out problems other than being something of a memory hog which, of course, slows things down somewhat.  But ... it hasn't crashed on me ... yet.  

However ... I am a fan of Firefox and am quite satisfied with it aside from the 'crashing' thing ... just wished 'they' would fix it!

---

### Post by Cowloon on 2006-06-05
Since upgrading from breezy to dapper, seamonkey that I had installed prior to the upgrade segfaults. Running seamonkey-installer to reinstall also segfaults. The plain tar.gz file from the seamonkey site, doesn't segfault, but it also doesn't present a window on the screen.

How do you diagnose a problem like this?

Luckily, I seem to have the same functionality, including the most important (being able to read my work email), using mozilla-1.7.12, so far.

---

### Post by bychan on 2007-01-08
Without having installed anything yesterday, firefox hasn't started today. I receive the message 
"Segmentation fault      "$prog" ${1+"$@"}"
I am not using Ubuntu but SuSE!
I encounter the same error message, if I try to start thunderbird!

I have reinstalled firefox from scratch and even moved my .mozilla directory to make sure that no extensions are causing this problem!

I really hope that somebody has found a fix in the meantime!

Bernard

---

### Post by wheaties_box on 2007-01-10
you might try removing your ~/.gtkrc-2.0 or ~/.gtk_qt_engine_rc files.... 

I use KDE (and I use Slackware) and I was trying to make the GTK-based applications have pretty fonts, but each time I tried to start up firefox after my hack it would segfault.  If I remove those files it loads fine.

Good luck!

---

### Post by mattotoole on 2007-02-13
I'm having the exact same problem, with the same terminal error message, with both Firefox and Swiftfox.

I can avoid the crashes by opening links in new tabs, but this is not a solution.

---

### Post by blaise69 on 2007-02-13
I'm having this problem with a fresh install of Xubuntu, I decided to check my LiveCD and it also has the same problem, I decided to download the Ubuntu LiveCD and again, I can't even open up Firefox, running it from Terminal brings up Segmentation Fault (Core Dump).

I upgraded Firefox to the latest in Synaptec, (smae problem) and I've installed Opera (same problem!)

Any ideas on why this happens?

Both LiveCd's were downloaded from the UK Bittorrent soruce,

Cheers,

Blaise.

---

### Post by believekevin on 2007-02-25
i just began to see this issue after updating both firefox and flash player.  i suspect it has something to do with flashplayer but i am not 100% sure.

this morning, i removed all version of firefox and mozilla as well as plugins and installed firefox 2 clean.  the segfault issue persists though i can't perfectly reproduce it.

---

### Post by believekevin on 2007-02-25
The seg fault occurs when you are LEAVING a page that uses the Flash plugin.  This can be tricky to repro simply because the plugin is called frequently in unexpected places.

See this thread on the Adobe Forums:
[http://www.adobe.com/cfusion/webforums/forum/messageview.cfm?catid=184&threadid=1242075&CFID=36717448&CFTOKEN=64e39f2a520999cc-FA4B149E-0535-4FE6-DE5A4E7CA6BFE780&jsessionid=1111eece3cb84c5c137b]("http://www.adobe.com/cfusion/webforums/forum/messageview.cfm?catid=184&threadid=1242075&CFID=36717448&CFTOKEN=64e39f2a520999cc-FA4B149E-0535-4FE6-DE5A4E7CA6BFE780&jsessionid=1111eece3cb84c5c137b")

---

### Post by lieutpigeon on 2007-03-02
I'm pretty new to Linux, so please view these comments in that light! 

I've had exactly the same problem as those described above, with Firefox quitting unexpectedly on accessing certain web pages. When I ran Firefox from the command line and redirected stderr messages to a file, I got:

Segmentation fault (on the screen)

and then  (from stderr)

LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: undefined symbol: XtCalloc]
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/nppdf.so [/usr/lib/firefox/plugins/nppdf.so: undefined symbol: XtCalloc]

I looked at the Adobe website thread referred to earlier in the thread, and it seems there is a problem with Flash player.

According to /usr/share/doc/flash-plugin-9.0.31.0/readme.txt, the way to disable Flash is to remove libflashplayer.so from your root or home browser plugins directory.

I did this, and found that the Firefox segmentation fault had gone away. It seems that you can have Firefox if you can live without Flash. Not a solution, but maybe a temporary work-around until whatever-it-is is fixed?

Better ideas welcomed!

---

### Post by wolkengold on 2007-07-19
I have the problem, that my firefox 2 with flash 9 on breezy crashes on some webpages.  When I start firefox and call first a page with a flash 7 movie and leave it open it doesn't happen any more. So I put on one of my [web pages a flash movie]("http://babelhost.net/143.0.html"), which I call as first action when I start firefox. After this I go on working in different tabs and leave the flash movie in the first tab all the time running. No more segmentation faults. Maybe it works at other people to.
:)

---

