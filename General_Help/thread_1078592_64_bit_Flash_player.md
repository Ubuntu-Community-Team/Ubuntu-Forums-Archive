---
title: "64 bit Flash player"
date: 2009-02-23
forum: General Help
---

### Post by lorgonjortle on 2009-02-23
Hello there,

I'm fairly new to Ubuntu, but I've recently installed 64 bit. I had 32 for a while. Everything's been going fine along the lines of getting the right software, but Flash player is giving me a heck of a hard time. I know some of you are thinking right now "Use the search feature, it does wonders!". I have. Nothing I've found has worked. I've tried three different tutorials. So any help would be great.

Acer aspire 5100
Radeon Xpress 1100
Hardy Heron 64 bit

---

### Post by mb_webguy on 2009-02-23
Uninstall the repository version of Flash -- all of them, in case you have Gnash or some other plugin installed.  Open "about:plugins" in Firefox to double-check that you don't have any Flash plugins installed.

Then go to the [Adobe website]("http://labs.adobe.com/downloads/flashplayer10.html") and download the 64-bit Linux plugin.  It's alpha release, but still pretty solid.  Put this in your ~/.mozilla/plugins directory.  You may need to create this directory.

Now restart Firefox, and you shouldn't have any more problems with Flash.

---

### Post by lorgonjortle on 2009-02-23
Yeah, I've done this before... still nothing. I removed the flash-nonfree thing, along with nsplugin. Then I copied the extracted .so file. Look here:

```
lorgonjortle@The-One:~/.mozilla/plugins$ ls -l
total 9320
-rwxr-xr-x 1 lorgonjortle lorgonjortle 9526312 2008-12-10 12:13 libflashplayer.so
lorgonjortle@The-One:~/.mozilla/plugins$ 

```

I then closed Firefox, and opened it again. It didn't work. I read somewhere that FireFox reads plugins from another folder.. I'll try that. I think it was /usr/lib/mozilla/plugins or something. As I said, I'm new to Linux, so I"m not sure. Thanks for the help so far.

---

### Post by mb_webguy on 2009-02-23
What does "about:plugins" say about Flash?

---

### Post by deepclutch on 2009-02-23
It is working fine here on 64-bit Intrepid.for me ,I downloaded and copied onto /usr/lib/firefox/plugins/ directory.but , ~/.mozilla/plugins/ dir also must be respected by firefox ?

---

### Post by lorgonjortle on 2009-02-23
It says nothing about Flash. Here's the whole thing:

```
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
iTunes Application Detector

    File name: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes
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
Totem Web Browser Plugin 2.22.1

    File name: libtotem-basic-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	- 	ogg 	Yes
application/ogg 	Ogg multimedia 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	- 	anx 	Yes
audio/annodex 	- 	axa 	Yes
video/annodex 	- 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealAudio document 	rpm 	Yes
VLC Multimedia Plugin (compatible Totem 2.22.1)

    File name: libtotem-cone-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-vlc-plugin 	unknown 		Yes
application/vlc 	unknown 		Yes
video/x-google-vlc-plugin 	unknown 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Microsoft ASX playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	QuickTime image 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes

```

Also, I copied that file into both ~/.mozilla/plugins and /usr/lib/mozilla/plugins and I get nothing. I even rebooted. :-\

---

### Post by deepclutch on 2009-02-23
EDIT:Did you download the 64-bit flash 10 beta Plugin-to be precise this:
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz)
you download the flash 10 beta ,(remember to purge libflashsupport ,it is not needed).extract libflashplayer.so to your /home/user/Desktop.where user is your home directory.
open a terminal and do as below:
```
sudo cp /home/user/Desktop/libflashplayer.so /usr/lib/firefox/plugins ;sudo cp /home/user/Desktop/libflashplayer.so /usr/lib/mozilla/plugins 
```Now ,restart firefox and see.

---

### Post by stchman on 2009-02-23
> **lorgonjortle said:**
> Hello there,

I'm fairly new to Ubuntu, but I've recently installed 64 bit. I had 32 for a while. Everything's been going fine along the lines of getting the right software, but Flash player is giving me a heck of a hard time. I know some of you are thinking right now "Use the search feature, it does wonders!". I have. Nothing I've found has worked. I've tried three different tutorials. So any help would be great.

Acer aspire 5100
Radeon Xpress 1100
Hardy Heron 64 bit

Follow my tutorial.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

---

### Post by fooman on 2009-02-23
don't know if it will help,  but you could just try copying it to /usr/lib/

i saw that posted somewhere once before,  like i said...not sure if it will help,  but it won't hurt.

---

### Post by lorgonjortle on 2009-02-23
Deepclutch, I did exactly as you said, and I still got nothing. I did it with Firefox closed, and when I opened it, YouTube still didn't work. stchman, I'll look at your tutorial now. thanks for all the responses

---

### Post by Moop on 2009-02-23
Check the usr/lib/mozilla/plugins folder for old broken links and delete them. I had a broken link in there after un-installing flashplugin-non-free and it was causing problems with firefox until I deleted it. 

I put the extracted flash file from adobe in ~/.mozilla/plugins and put a link to that in usr/lib/mozilla/plugins and everything works fine.

---

### Post by lorgonjortle on 2009-02-23
No luck on that tutorial. I followed everything, but Youtube still says I don't have Flashplayer. Fooman, I'll try yours, thanks.

---

### Post by lorgonjortle on 2009-02-23
Moop, how does one link?

---

### Post by Moop on 2009-02-23
> **lorgonjortle said:**
> Moop, how does one link?

You can right click on the file you want to link to and create a link. Then move the link to wherever you want.

---

### Post by lorgonjortle on 2009-02-23
I did as you said for the linking. That didn't do anything either. I had Firefox closed when I did it too. ugh Any more ideas?

---

### Post by steveneddy on 2009-02-23
Here we go again:

First perform each one of these commands individually in terminal:

```
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo apt-get purge flashplugin-nonfree
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```

Then download the flash player from adobe:

Click the link:

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz)

Put it on your desktop.

Extract the .tar.gz by right clicking and selecting "Extract Here"
You should see a file called "libflashplayer.so"

Open a terminal and go to the Desktop:

```
cd ~/Desktop
```Now you need to put it in the correct folders for it to work correctly:

```
sudo cp libflashplayer.so /usr/lib/firefox-addons/plugins/ /usr/lib/mozilla/plugins/
```Restart Firefox and you should be set.

**If you have copied some [COLOR=Red]Flash.so[/COLOR] file anywhere in your system and the first set of commands did not delete it, then manually do so before installing any other version of Flash or it will not work.**

---

### Post by deepclutch on 2009-02-23
why not you do this? log out of your session and login again? :) try if it works(X restarts).

---

### Post by lorgonjortle on 2009-02-24
steveneddy, I got closer. I read through your post first, and noticed at the bottom you said yo remove any other *flash*.so. So I did a search of my filesystem for them. Turns out I had one hidding in /usr/lib/firefox-addons/plugins. So I followed all of your steps, but still no Flash. I made sure the files were copied to the correct locations, and after that didn't work, I tried copying it to ~/.mozilla/plugins. Still with no avail. What should I do? Retry the steps, or maybe I need a restart? I'll restart... and we'll see. Thanks for all the help.

Lorgon Jortle

---

### Post by lorgonjortle on 2009-02-24
Alright, I did the whole thing over again, this time going into nautilus afterwards and checking twice that everything was right. I also found, while doing a search for *flash*.so, this: /usr/lib/openoffice/program/libflash680lx.so but I figured by the looks that it was ok to keep. Flash is still not working. Any more ideas?

---

### Post by deepclutch on 2009-02-24
> Flash is still not working. Any more ideas?
Copy the libflashplayer.so (64-bit flashplayer 10 beta) to:
```
sudo cp libflashplayer.so /usr/lib/firefox-3.0.6/plugins/ 
```

---

### Post by lorgonjortle on 2009-02-24
Negative on that one. I'm losing my mind man. Half of my site is through YouTube, and I can't view anything. Thanks for all of the help so far though, I know it doesn't make much sense. :mad:

---

### Post by SuperSonic4 on 2009-02-24
What about

```
sudo apt-get purge flashplugin-nonfree
```

```
sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so
```

note you should extract the archive from adobe to your desktop for this to work.

Source: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by lorgonjortle on 2009-02-24
Nope on that one. I went ahead and switched back to 32 bit. It wasn't worth it going 64. It's fine though. Thanks for all the help everyone. Hopefully Adobe will hurry up and the stable release will be easier to install. I'm looking to try 64 bit on my new computer.

Lorgon Jortle

---

### Post by steveneddy on 2009-02-26
You can find all instances of Flash player by opening up a terminal and

```
locate libflashplayer.so
```Here's where I put mine:

> /usr/lib/firefox/plugins/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/firefox-3.0.6/pluginsI don't know why four folders, but Flash 10 shows up in about:plugins in FF.

Flash works for me perfectly. I use Hardy 64 bit and FF 3.06.

If you can't get it working, manually remove all Flash.so files in your system and install Flash from the repos.

```
sudo apt-get install flashplugin-nonfree
```It's really not that hard in my opinion.

Use the locate function and find and delete Flash, put it in the folders listed above.

You should just have to put it in the folder with 3.06 in the title, but it seems to work better if it is in all four folders IMHO.

This is just my .02

I hope this helps.

---

### Post by dLeon on 2009-02-26
I'm a 32bit user, so don't know if this will work. I'm not using adobe flash plugin. I'm not do in depth check which plugin responsible, still .SWF/.FLV work for me.
In firefox I notice that it use Totem/Gstreamer plugins + Mplayer plugins for multimedia. I test firefox to open net & local .SWF file, & it just work. Don't know if the flash file you mean is .FLV. I never play streaming media in Firefox or even IE. Although, .FLV movie do run in my local system.
Gstreamer available in main repos. Mplayer is medibuntu's. Also try to W32codec (medibuntu); seems it contains some of Windows(tm) media dll's.

---

### Post by DeMus on 2009-02-26
I use this site to install flash:
[http://www.howtoforge.com/installing-adobe-flash-10-on-a-64bit-ubuntu-8.04]()

Maybe you have done all of this already so this also might not work, for me it did work. Don't ask me why, I don't know why there ar any differences between several installations.

---

