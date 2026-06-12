---
title: "Firefox 3 sometimes slow - grey screen, slow tabs"
date: 2008-12-12
forum: General Help
---

### Post by KhipuX on 2008-12-12
Can't find a bug for this yet so I'd just thought I'd check with you folks before I reported one.

I have Ubuntu 8.10 with Firefox 3.0.4. Everything was working fine until the last three weeks. Now, on occasions it takes an age (up to 2 minutes!) to switch tabs in Firefox. Sometimes the screen goes greyscale and the machine freezes for about 40 seconds or so. It seems to be getting more frequent.

Anybody else have the same problem? I can't seem to figure out what the computer is doing in the background that takes so long.

---

### Post by pedro_orange on 2008-12-12
Are you using flash when you experience these problems?
Are you using sound?

You must narrow down what are you using besides firefox.

---

### Post by KhipuX on 2008-12-15
No Flash, no sound. I've got Flash installed and I tried uninstalling it but I still get the same problem. My sound is Intel HDA and has never worked since 6.10 so I don't bother using it anymore.

I made sure that the only thing running is Firefox (application-wise) and checked through all the processes to make sure nothing was starting without me knowing. Still got the problem though.

---

### Post by hikaricore on 2008-12-15
Try turning off desktop effects, your hardware may not be able to handle them correctly.

Let us know if this makes any difference.

---

### Post by dimanche on 2009-02-03
I'm getting the same problem.

For example: I open a web page that has about 20 thumbnails, I right click> open in new tab for each thumbnail. After about 7 tabs firefox seems to hang.

This is very strange, can anyone shed any light?

EDIT: hikaricore I have tried turning off desktop effects and there is no change

---

### Post by Yashiro on 2009-02-03
Unless you post what versions of the OS you are running and what plugins you use, no one can help.

---

### Post by dimanche on 2009-02-03
> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
Linux ubuntu 2.6.27-11-generic

Plugins for Firefox? ...
> Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r15

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
Picasa

    File name: npPicasa3.so
    Picasa plugin

MIME Type 	Description 	Suffixes 	Enabled
application/x-picasa-detect 	3.0 	pinstall 	Yes
Totem Web Browser Plugin 2.24.3

    File name: libtotem-basic-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	Ogg multimedia file 	ogg 	Yes
application/ogg 	Ogg multimedia file 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	application/annodex type 	anx 	Yes
audio/annodex 	audio/annodex type 	axa 	Yes
video/annodex 	video/annodex type 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
application/x-totem-plugin 	Totem Multimedia plugin 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

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
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
IcedTea Web Browser Plugin

    File name: IcedTeaPlugin.so
    The IcedTea Web Browser Plugin executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
VLC Multimedia Plug-in

    File name: libvlcplugin.so
    Version 0.9.4 Grishenko, copyright 1996-2007 The VideoLAN Team
    [http://www.videolan.org/](http://www.videolan.org/)

MIME Type 	Description 	Suffixes 	Enabled
audio/mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
audio/x-mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
video/mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/x-mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/x-mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/mp4 	MPEG-4 video 	mp4,mpg4 	Yes
audio/mp4 	MPEG-4 audio 	mp4,mpg4 	Yes
application/mpeg4-iod 	MPEG-4 video 	mp4,mpg4 	Yes
application/mpeg4-muxcodetable 	MPEG-4 video 	mp4,mpg4 	Yes
video/x-msvideo 	AVI video 	avi 	Yes
video/quicktime 	QuickTime video 	mov,qt 	Yes
application/x-ogg 	Ogg stream 	ogg 	Yes
application/ogg 	Ogg stream 	ogg 	Yes
application/x-vlc-plugin 	VLC plug-in 	vlc 	Yes
video/x-ms-asf-plugin 	Windows Media Video 	asf,asx 	Yes
video/x-ms-asf 	Windows Media Video 	asf,asx 	Yes
application/x-mplayer2 	Windows Media 		Yes
video/x-ms-wmv 	Windows Media 	wmv 	Yes
video/x-ms-wvx 	Windows Media Video 	wvx 	Yes
application/x-google-vlc-plugin 	Google VLC plug-in 		Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/3gpp 	3GPP audio 	3gp,3gpp 	Yes
video/3gpp 	3GPP video 	3gp,3gpp 	Yes
audio/3gpp2 	3GPP2 audio 	3g2,3gpp2 	Yes
video/3gpp2 	3GPP2 video 	3g2,3gpp2 	Yes
video/divx 	DivX video 	divx 	Yes
video/flv 	FLV video 	flv 	Yes
video/x-flv 	FLV video 	flv 	Yes
video/x-matroska 	Matroska video 	mkv 	Yes
audio/x-matroska 	Matroska audio 	mka 	Yes
Adobe Reader 8.0

    File name: nppdf.so
    The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.

MIME Type 	Description 	Suffixes 	Enabled
application/pdf 	Portable Document Format 	pdf 	Yes
application/vnd.fdf 	Acrobat Forms Data Format 	fdf 	Yes
application/vnd.adobe.xfdf 	XML Version of Acrobat Forms Data Format 	xfdf 	Yes
application/vnd.adobe.xdp+xml 	Acrobat XML Data Package 	xdp 	Yes
application/vnd.adobe.xfd+xml 	Adobe FormFlow99 Data File 	xfd 	Yes
Java(TM) Plug-in 1.6.0_10-b33

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_10

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
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_10 	Java 		Yes
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
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_10 	Java 		Yes

I'v only been using ubuntu for a few days now, so I'm a total newbe. I hope this is what your looking for :S

---

### Post by Yashiro on 2009-02-03
I'd definitely start by uninstalling Flashplayer, Icedtea(Java) and VLC plugins. Run without them for a few days. All three of those plugins have been seen to cause the issues you describe. (flash and java moreso than vlc)

---

### Post by Superdarion on 2009-02-04
> **Yashiro said:**
> I'd definitely start by uninstalling Flashplayer, Icedtea(Java) and VLC plugins. Run without them for a few days. All three of those plugins have been seen to cause the issues you describe. (flash and java moreso than vlc)
So you suggest we navigate with no flash nor java...

That looks more like a Microsoft approach (if some necessary feature is unsafe/unstable, prevent the user from using it instead of fixing it) and I for one am not willing to do that.

Any other way to get around that? Because I suffer the same illness.



---------Edit--------
Ok, Icedtea is Java, not javascript, I didn't notice that; so I can disable that without messing many of my usual sites.

---

### Post by Yashiro on 2009-02-04
It's called eliminating potential causes. How else can someone else via the internet diagnose such a vague problem? If the issues cease, then we know where to start.

[I][size=1]"I have a problem, I'll ask someone on the internet."
"Hey this guy wants me to perform some basic troubleshooting."
"Screw that, that's the Microsoft way."
<internet helper leaves thread> [/size][/I]

---

### Post by networm1230 on 2009-02-04
Hello to All. I have found a web site that helped me hear it is [http://howto.helpero.com/howto/Speed-Up-Firefox_31.html](http://howto.helpero.com/howto/Speed-Up-Firefox_31.html)

Note: if it dos not help you you can try a reinstall!

---

### Post by dimanche on 2009-02-04
> **networm1230 said:**
> Hello to All. I have found a web site that helped me hear it is [http://howto.helpero.com/howto/Speed-Up-Firefox_31.html](http://howto.helpero.com/howto/Speed-Up-Firefox_31.html)

Note: if it dos not help you you can try a reinstall!

This did not solve the problem.


I have found a thread on another forum that details the problem I am having.

> [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/187313](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/187313)

It seems when using firefox and you open so many tabs by using the 'right clcik>open in new tab' feature firefox becomes very slow and it starts doing strange things, please see link above. Does anyone know why? or more important does anyone have the same problem?

---

### Post by networm1230 on 2009-02-04
> **dimanche said:**
> This did not solve the problem.


I have found a thread on another forum that details the problem I am having.



It seems when using firefox and you open so many tabs by using the 'right clcik>open in new tab' feature firefox becomes very slow and it starts doing strange things, please see link above. Does anyone know why? or more important does anyone have the same problem?

bummer! I have never had this right clicking problem. So I do not think that I could help you with this problem. I will try to do some research on this problem for you.

---

### Post by gacolek on 2009-02-05
> **dimanche said:**
> This did not solve the problem.


I have found a thread on another forum that details the problem I am having.



It seems when using firefox and you open so many tabs by using the 'right clcik>open in new tab' feature firefox becomes very slow and it starts doing strange things, please see link above. Does anyone know why? or more important does anyone have the same problem?

I also have the same problem what you have, but funny thing is, that when you install IceWeasel or IceCat which based on the same engine what Firefox, they work with no problem. I also do not know how Firefox hangs so :/ It is very annoying for me :/ I also try speed up Firefox according to advices gives in link, but it does not solve this problem. Anyone have an idea what we need to do? With Opera I also do not have that kind of problem.

---

### Post by dimanche on 2009-02-05
yeah its very annoying. But no one has a solution. I wonder what is causing it, Firefix or Ubuntu?

Where is Chrome!

---

### Post by philinux on 2009-02-05
I'm not having this problem 64 or 32 bit, and I'm using compiz. I would suggest running firefox in safe mode

```
firefox -safe-mode
```

It could be an addon or two that's the cause. Other thing to try is to backup your bookmarks and delete the .mozilla folder and create a new profile.

---

### Post by fig_wright on 2009-03-02
I am having this problem too. Seems this has been going on for 2 years at least and there is no solution yet :mad:

Covered here:
[http://ubuntuforums.org/showthread.php?t=590242](http://ubuntuforums.org/showthread.php?t=590242)
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/226878](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/226878)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/172419](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/172419)

---

### Post by fig_wright on 2009-03-02
<deleted>

---

### Post by Guilden_NL on 2009-03-03
Aha!  Yes, this is exactly what is happening with my wife's laptop.

She refuses to use Linux/Ubuntu because it is "100 times slower than Vista #-o " and she's right.  It's because 80% of what she does is browser based.  I finally took some time tonight and decided that I'd rather go back to Windows 3.11 than work under Ubuntu if it acted this way for me.  I messed around with various logging tools (still years behind MSFT......) and finally nuked the Firefox session and it turned into a Ferrari.  I was trying to work as she did, hence my not rebooting, going through the normal troubleshooting process.  It sneaked into Firefox on this laptop sometime around Dec 1.

I'll be trying various browsers and the workarounds to see if any work. 

It's especially annoying since I am 100% Linux in our house and my wife now refuses to use it.

---

### Post by HuaiDan on 2009-03-03
Here's a flash fix for Firefox on Ubuntu 64 that saved the grayscale problem for me.

[Link]("http://ubuntuforums.org/showthread.php?t=1081964")

The problem I experienced was embedded video opening gray and getting audio output only, among other annoyances.

As for the slow tabs and such, I'm not certain. How's your hardware? I've seen Firefox run well in Ubuntu on some pretty skimpy HW.
Have you tried deleting your firefox profile? Just close firefox and send /home/~/.mozilla to the trash.  Firefox will recreate it next time you start it. I've also solved some FF issues that way.

---

