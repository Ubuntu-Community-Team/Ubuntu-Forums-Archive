---
title: "Flash 10"
date: 2009-04-11
forum: Desktop Environments
---

### Post by andrea000 on 2009-04-11
I have only had flash up and running a week or so then 
today i downloaded systems updates after installing a
desktop search tool called beatle now flash is not
working.So i go to adobe's download page to try 
reinstalling but it says that a later version
is already installed.Flash never ran like it did
when i run windows it was always slow or i had to
click the arrow to get it to work can someone please
help me i cant even uninstall it
please

---

### Post by 3rdalbum on 2009-04-11
I have no idea why your Flash isn't working, but you're probably asking for trouble a little bit... Ubuntu already comes with a search and indexing tool called Tracker. Installing Beagle as well is likely to cause you some problems, or at least make everything slow.

---

### Post by andrea000 on 2009-04-11
ok i uninstalled beagle and i did not have deskbar app 
installed.I added the repo's to flash 10 and have that 
installed but it still does not work.

---

### Post by djbushido on 2009-04-11
How does it "not work"? Is there any error messages generated? What are you trying to run with flash? Also, try going to synaptic and reinstalling flash.

---

### Post by andrea000 on 2009-04-11
> **djbushido said:**
> How does it "not work"? Is there any error messages generated? What are you trying to run with flash? Also, try going to synaptic and reinstalling flash.

no error messages.I am trying to watch youtube and hulu no luck with 
it.I tried uninstalling and reinstalling then rebooting and updating
the video driver it didn't work.I would like to run Miro and Banshee
but i need flash for both of these.

---

### Post by djbushido on 2009-04-11
Are you using the repo or Adobe? If not Adobe, try using that, check their site. Also, try running a flash app from terminal. For example, "gnome-terminal -e banshee". Post back what this says.

---

### Post by andrea000 on 2009-04-11
> **djbushido said:**
> Are you using the repo or Adobe? If not Adobe, try using that, check their site. Also, try running a flash app from terminal. For example, "gnome-terminal -e banshee". Post back what this says.

here is the my Miro log 

location: /usr/lib/xulrunner-1.9.0.8/libxpcom.so 
before 3
2009-04-11 18:54:32,932 INFO     Starting up Miro
2009-04-11 18:54:32,936 INFO     Version:    2.0.4
2009-04-11 18:54:32,963 INFO     OS:         Linux 2.6.24-23-generic i686
2009-04-11 18:54:32,966 INFO     Revision:   [https://svn.participatoryculture.org/svn/dtv/tags/Miro-2.0.4/tv/resources](https://svn.participatoryculture.org/svn/dtv/tags/Miro-2.0.4/tv/resources) - 9360
2009-04-11 18:54:32,971 INFO     Builder:    pbuilder@mercury
2009-04-11 18:54:32,980 INFO     Build Time: 1238973852.79
2009-04-11 18:54:32,982 INFO     Starting event loop thread
2009-04-11 18:54:33,051 INFO     Python version:    2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)]
2009-04-11 18:54:33,073 INFO     Gtk+ version:      (2, 12, 9)
2009-04-11 18:54:33,074 INFO     PyGObject version: (2, 14, 2)
2009-04-11 18:54:33,077 INFO     PyGtk version:     (2, 12, 1)
2009-04-11 18:54:33,086 INFO     Language:          [('LANG', 'en_US.UTF-8')]
2009-04-11 18:54:33,090 INFO     set_renderer: trying to add gstreamerrenderer
2009-04-11 18:54:33,628 INFO     GStreamer version: GStreamer 0.10.18
2009-04-11 18:54:33,729 INFO     GStreamer videosink: gconfvideosink
2009-04-11 18:54:33,735 INFO     GStreamer audiosink: gconfaudiosink
2009-04-11 18:54:33,777 INFO     set_renderer: successfully loaded gstreamerrenderer
2009-04-11 18:54:33,920 INFO     Restoring database...
2009-04-11 18:54:33,926 INFO     Connecting to /home/me/.miro/sqlitedb
2009-04-11 18:54:35,257 TIMING   Database load slow: 1.331
2009-04-11 18:54:35,259 INFO     Database size on disk (in bytes): 747520
2009-04-11 18:54:35,260 INFO     Database object count: 121
2009-04-11 18:54:36,492 TIMING   idle (finish startup) too slow (3.440 secs)
2009-04-11 18:54:36,500 INFO     Checking movies directory '/home/me/.miro/Movies/'...
2009-04-11 18:54:40,967 TIMING   WARNING: Calling <bound method ChannelGuide.guide_downloaded of <miro.guide.ChannelGuide instance at 0x8b720ac>> on HTTPClient: [http://www.hulu.com/videos/search?query=Stargate+SG-1](http://www.hulu.com/videos/search?query=Stargate+SG-1) too slow (1.895 secs)
2009-04-11 18:54:42,298 TIMING   WARNING: Calling <bound method ChannelGuide.guide_downloaded of <miro.guide.ChannelGuide instance at 0x8969fcc>> on HTTPClient: [http://beta.legaltorrents.com/](http://beta.legaltorrents.com/) too slow (1.227 secs)
2009-04-11 18:54:44,341 INFO     Starting auto downloader...
2009-04-11 18:54:44,442 TIMING   Icon clear: 0.000
2009-04-11 18:54:44,443 INFO     Starting movie data updates
2009-04-11 18:54:44,473 INFO     Checking for updates...
2009-04-11 18:54:44,742 INFO     No updates for this platform.


i installed the adobe flash from there web site but i tried the one in the repo's as well none of them worked

---

### Post by archolman on 2009-04-11
[SIZE=3]I also am having trouble with flash10.
I have re-installed via synaptic, etc.
The return I get from the piece of code that you gave andrea is  "There was an error creating the child process for this terminal"
 in an error box, in a new terminal.
[/SIZE]

---

### Post by djbushido on 2009-04-11
From just that it looks like the problem is with the program, not flash.
Try re-installing the program as well.
Also, check if there is a program debug mode, usually run with "<some_program> --debug" or try "<some_program> --help" and see if that says anything about a debug. Post the results of that back, because it looks like the flash problem is no fault of flash. Currently.

---

### Post by andrea000 on 2009-04-11
So were could the problem be?I can't play flash on 
websites as well.I have also tried flash from synaptic 
as well with no luck.Could firefox be the problem?

---

### Post by andrea000 on 2009-04-11
no luck with debug program on this piece of software.

---

### Post by andrea000 on 2009-04-11
Here is the log file when i do a (about plug ins) on Firefox.
I myself do not see a flash plug in but i do not know if it
should show up in this kind of log.I see a shockwave-flash
but it soes not make a difference if its on or off i un 
installied shockwave but i had the same effect.


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
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealAudio document 	rpm 	Yes
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
iTunes Application Detector

    File name: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r22

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by andrea000 on 2009-04-12
has anyone else had a problem like what i am having.
I can verify flash is installed but it does not work
on anything.

---

### Post by archolman on 2009-04-12
[SIZE=3]Andrea, yes, I can't get Flash to run either... I want to view BBC News pages & some Youtube vids, no joy with either. Any one else got a clue?

* output of about:config
[/SIZE]**Shockwave Flash**

 File name:  libflashplayer.so Shockwave Flash 10.0 r22   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes
[SIZE=3] 
[/SIZE]

---

### Post by andrea000 on 2009-04-12
> **archolman said:**
> [SIZE=3]Andrea, yes, I can't get Flash to run either... I want to view BBC News pages & some Youtube vids, no joy with either. Any one else got a clue?

* output of about:config
[/SIZE]**Shockwave Flash**

 File name:  libflashplayer.so Shockwave Flash 10.0 r22   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes
[SIZE=3] 
[/SIZE]

I know how you feel but i need mine to connect to my 
office network they have a new terminal server and 
it requires flash 9 or higher i dont know i run 
windows and autocad on virtual box but all the other
stuff i have coming to my main desktop.I don't know 
what i am going to do about flash.

---

### Post by djbushido on 2009-04-12
Um, this shows that you installed shockwave flash. Try going to Adobe and installing it.
Also, did you run Firefox in debug mode? If not, try that.

---

### Post by andrea000 on 2009-04-12
ok i need some help on this one adobe's website says there is 
no shockwave player for linux but i seem to have one installed 
as a add on to firefox i remember installing this from
the mozilla website so my question is how do i get rid of it
that is most likely were the problem is if there is not a version
for ubuntu.I am running 8.04 in case anyone needs to know.

---

### Post by archolman on 2009-04-12
[SIZE=3] I am only using flash as a browser plug-in, not as an app.. Sorry for any confusion.
  However, how do I run Firefox in debug mode? and, I have checked in Synaptic for, found & re-installed, Flash 10 & it's installer. 
[/SIZE]

---

### Post by andrea000 on 2009-04-12
I to need to know how to run it in debug mode?Also i am trying to 
uninstall shock wave flash firefox plugin adobe says there is no 
plugin for ubuntu i don't know how it installed i remember adding
it at mozilla's web site.I have found were it is installed here 
is were /usr/lib/swfdec-mozilla/libswfdecmozilla.I tried rm on it
if i did it right so how would i get rid of it?

Thanks

---

### Post by djbushido on 2009-04-12
There is no shockwave for linux. Period.
Just install the adobe plugin, it will write over the shockwave plugin, or whatever. Just do it.
Also, the debug mode for firefox is ```
firefox --debug
```

---

### Post by andrea000 on 2009-04-12
did that just opens firefox up nothing changed 
flash still doesn't work.

---

### Post by sharathpaps on 2009-04-12
I have exactly the same problem. I tried everything - completely removing, reinstalling Flash and Firefox too. Its been of no use. Firefox reports that the flash plugins are installed and working (see attachment) .I still get those grey boxes wherever I go. I got so tired of it that I've temporarily stopped using Firefox. Alternate browsers like Opera and Epiphany also have the same problem. 

So now I'm using Flock. You can download the .deb package from [GetDeb]("http://www.getdeb.net/download/3635/0") . For some reason, flash works perfectly well in Flock even when the other browsers don't.

On a side note : The upside of the whole situation is that, now, I've realized how much flash content websites use. Some websites are grey boxes all over. Anyone would be crippling their browsing experience without a flash enabled browser.

---

### Post by djbushido on 2009-04-12
Well if something like that is working, it is not the fault of Flash.
I have nothing more to say than re-install, this behavior is extremely weird...
Sorry I couldn't be of more help.

---

### Post by andrea000 on 2009-04-12
There is no shockwave player plug in i do not
know how it got on my pc but i cant even
uninstall it this is what i get when i go to
adobe's website to try and download it. 

Sorry, your platform is not supported.

can someone tell me how to get rid of it it's
in this directory and is installed as a plug in

/usr/lib/swfdec-mozilla/libswfdecmozilla.so


anyway this is were i got the plugin at 

[https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7)

---

### Post by andrea000 on 2009-04-12
> **sharathpaps said:**
> I have exactly the same problem. I tried everything - completely removing, reinstalling Flash and Firefox too. Its been of no use. Firefox reports that the flash plugins are installed and working (see attachment) .I still get those grey boxes wherever I go. I got so tired of it that I've temporarily stopped using Firefox. Alternate browsers like Opera and Epiphany also have the same problem. 

So now I'm using Flock. You can download the .deb package from [GetDeb]("http://www.getdeb.net/download/3635/0") . For some reason, flash works perfectly well in Flock even when the other browsers don't.

On a side note : The upside of the whole situation is that, now, I've realized how much flash content websites use. Some websites are grey boxes all over. Anyone would be crippling their browsing experience without a flash enabled browser.

Solved this fo me anyway.I learned shockwave flash was the 
problem it is a plug in for firefox but adobe does not make
a shock wave plugin for Linux so first  i took flash off then 
i had to go to the directory were shockwave was installed
and delete it fire fox doesn't let you delete plug in's
then reinstall flash 10.

---

### Post by djbushido on 2009-04-13
Shockwave and flash are two completely different things. Let's make that clear.
So do you have firefox working now? If not, install the ADOBE FLASH plugin not the ADOBE SHOCKWAVE plugin.

---

### Post by andrea000 on 2009-04-13
> **djbushido said:**
> Shockwave and flash are two completely different things. Let's make that clear.
So do you have firefox working now? If not, install the ADOBE FLASH plugin not the ADOBE SHOCKWAVE plugin.

yes flash works great now i had to delete shockwave flash
the plug in would not let me uninstall it but flash is
working now i even upgraded from 8.04 to 8.10 with no
problem.Thank you for all your help.

---

### Post by archolman on 2009-04-15
[SIZE=3] I finally tracked down the "Shockwave" entry in synaptic, deleted it all, & re-installed "Flash". It now works, & I can log-on to my gas & electric accounts, apart from watching BBC News & YouTube. 
Thanks to all for the help. 
it's good to talk:-)
[/SIZE]

---

### Post by andrea000 on 2009-04-15
> **archolman said:**
> [SIZE=3] I finally tracked down the "Shockwave" entry in synaptic, deleted it all, & re-installed "Flash". It now works, & I can log-on to my gas & electric accounts, apart from watching BBC News & YouTube. 
Thanks to all for the help. 
it's good to talk:-)
[/SIZE]

sorry i didn't get what you was saying right off

---

