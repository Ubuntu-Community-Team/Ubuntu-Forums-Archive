---
title: "Realplayer firefox plugin problem"
date: 2005-12-11
forum: Desktop Environments
---

### Post by Rory on 2005-12-11
On (K)Ubuntu Hoary 5.04, if I clicked on a RealPlayer link, like here: [http://www.cbc.ca/national/](http://www.cbc.ca/national/) (Watch the National), RealPlayer would pop up and play it. For .mov links like at apple.com/trailers/, the MPlayer plugin would take priority. Everything just worked.

In (K)Ubuntu Breezy, the mplayer-plugin in Firefox 1.5 takes priority on the cbc site and others for Real media files and then just chokes on the file and never plays it.

I have the PLF repo RealPlayer10 loaded. It works and if I grab the ram file from the cbc site or others, open RealPlayer and run it from there, without firefox1.5 as a middleman, it works. So, it appears to be Firefox related.

In KDE 3.5, I've changed the Preference Order under File Associations so Real file format pulls up Real player not MPlayer. But, this doesn't have an effect in Firefox.

I've uninstalled Real and installed it again. Plugins in the Mozilla libraries disappear and then reappear correctly. But the reinstall hasn't helped.

The two RealPlayer firefox helix plugins (.so and .xpt) are in the /usr/lib/mozilla-firefox/ and usr/lib/mozilla/ folders.

So, as you can see, I've been Googling and exhausted the avenues I can find but I keep coming up empty.


Can anyone lend their expertise?

Rory

---

### Post by Hairy_Palms on 2005-12-11
you could copy the realplayer codecs to /usr/lib/win32 so that mplayer can play the realmedia files. then mplayer will be able to play them,

---

### Post by Rory on 2005-12-11
I would prefer if I could launch the RealPlayer from Firefox automatically, like it did in Hoary Firefox 1.0.7.  It allows me to pause, and zip forward/backward with greater ease.  Mplayer plugin is too limiting for streaming files any longer than a couple of minutes.

As for moving the codecs over from Real library to /usr/win32, I'm pretty sure that library already has some Real codecs.  Although, this isn't a bad idea, for a short-term gap.  

What would the best terminal command for this?  This?
```
sudo cp -R /usr/lib/realplay-10.0.6.776/codecs/*.* /usr/lib/win32
```


The codecs are from the win32codec PLF package.  See below for comparison:

**Real codecs:**
```

/usr/lib/realplay-10.0.6.776/codecs/amrn.so
/usr/lib/realplay-10.0.6.776/codecs/amrw.so
/usr/lib/realplay-10.0.6.776/codecs/atrc.so
/usr/lib/realplay-10.0.6.776/codecs/colorcvt.so
/usr/lib/realplay-10.0.6.776/codecs/cook.so
/usr/lib/realplay-10.0.6.776/codecs/cvt1.so
/usr/lib/realplay-10.0.6.776/codecs/drv1.so
/usr/lib/realplay-10.0.6.776/codecs/drv2.so
/usr/lib/realplay-10.0.6.776/codecs/drvc.so
/usr/lib/realplay-10.0.6.776/codecs/raac.so
/usr/lib/realplay-10.0.6.776/codecs/rv10.so
/usr/lib/realplay-10.0.6.776/codecs/rv20.so
/usr/lib/realplay-10.0.6.776/codecs/rv30.so
/usr/lib/realplay-10.0.6.776/codecs/rv40.so
/usr/lib/realplay-10.0.6.776/codecs/sipr.so
/usr/lib/realplay-10.0.6.776/codecs/ddnt.so.6.0
/usr/lib/realplay-10.0.6.776/codecs/dnet.so.6.0
```


**Win32codecs:**
```

/usr/lib/codecs/acelpdec.ax
/usr/lib/codecs/alf2cd.acm
/usr/lib/codecs/aslcodec_dshow.dll
/usr/lib/codecs/aslcodec_vfw.dll
/usr/lib/codecs/asusasv2.dll
/usr/lib/codecs/asusasvd.dll
/usr/lib/codecs/ativcr2.dll
/usr/lib/codecs/atrac3.acm
/usr/lib/codecs/atrc.so.6.0
/usr/lib/codecs/AvidQTAVUICodec.qtx
/usr/lib/codecs/avimszh.dll
/usr/lib/codecs/avizlib.dll
/usr/lib/codecs/BeHereiVideo.qtx
/usr/lib/codecs/CLRVIDDC.DLL
/usr/lib/codecs/clrviddd.dll
/usr/lib/codecs/cook.so
/usr/lib/codecs/cook.so.6.0
/usr/lib/codecs/ctadp32.acm
/usr/lib/codecs/CtWbJpg.DLL
/usr/lib/codecs/ddnt.so.6.0
/usr/lib/codecs/DECVW_32.DLL
/usr/lib/codecs/divxa32.acm
/usr/lib/codecs/divx_c32.ax
/usr/lib/codecs/divxc32.dll
/usr/lib/codecs/divxdec.ax
/usr/lib/codecs/divx.dll
/usr/lib/codecs/dnet.so.6.0
/usr/lib/codecs/drv2.so.6.0
/usr/lib/codecs/drv3.so.6.0
/usr/lib/codecs/drv4.so.6.0
/usr/lib/codecs/drvc.so
/usr/lib/codecs/dspr.so.6.0
/usr/lib/codecs/huffyuv.dll
/usr/lib/codecs/i263_32.drv
/usr/lib/codecs/iac25_32.ax
/usr/lib/codecs/iccvid.dll
/usr/lib/codecs/icmw_32.dll
/usr/lib/codecs/imaadp32.acm
/usr/lib/codecs/imc32.acm
/usr/lib/codecs/ir32_32.dll
/usr/lib/codecs/ir41_32.dll
/usr/lib/codecs/ir50_32.dll
/usr/lib/codecs/ivvideo.dll
/usr/lib/codecs/jp2avi.dll
/usr/lib/codecs/l3codeca.acm
/usr/lib/codecs/l3codecx.ax
/usr/lib/codecs/LCMW2.dll
/usr/lib/codecs/LCodcCMP.dll
/usr/lib/codecs/LCODCCMW2E.dll
/usr/lib/codecs/lhacm.acm
/usr/lib/codecs/lsvxdec.dll
/usr/lib/codecs/m3jp2k32.dll
/usr/lib/codecs/m3jpeg32.dll
/usr/lib/codecs/m3jpegdec.ax
/usr/lib/codecs/mcdvd_32.dll
/usr/lib/codecs/mcmjpg32.dll
/usr/lib/codecs/mi-sc4.acm
/usr/lib/codecs/mpg4c32.dll
/usr/lib/codecs/mpg4ds32.ax
/usr/lib/codecs/msadp32.acm
/usr/lib/codecs/msg711.acm
/usr/lib/codecs/msgsm32.acm
/usr/lib/codecs/msh261.drv
/usr/lib/codecs/msms001.vwp
/usr/lib/codecs/msnaudio.acm
/usr/lib/codecs/msrle32.dll
/usr/lib/codecs/msscds32.ax
/usr/lib/codecs/msvidc32.dll
/usr/lib/codecs/mvoiced.vwp
/usr/lib/codecs/nsrt2432.acm
/usr/lib/codecs/pclepim1.dll
/usr/lib/codecs/qdv.dll
/usr/lib/codecs/qpeg32.dll
/usr/lib/codecs/qtmlClient.dll
/usr/lib/codecs/QuickTimeEssentials.qtx
/usr/lib/codecs/QuickTimeInternetExtras.qtx
/usr/lib/codecs/QuickTime.qts
/usr/lib/codecs/rt32dcmp.dll
/usr/lib/codecs/scg726.acm
/usr/lib/codecs/sipr.so.6.0
/usr/lib/codecs/sp5x_32.dll
/usr/lib/codecs/tm20dec.ax
/usr/lib/codecs/tokf.so.6.0
/usr/lib/codecs/tokr.so.6.0
/usr/lib/codecs/tsccvid.dll
/usr/lib/codecs/tsd32.dll
/usr/lib/codecs/tssoft32.acm
/usr/lib/codecs/tvqdec.dll
/usr/lib/codecs/ubv263d+.ax
/usr/lib/codecs/ubvmp4d.dll
/usr/lib/codecs/ultimo.dll
/usr/lib/codecs/VDODEC32.dll
/usr/lib/codecs/vdowave.drv
/usr/lib/codecs/vgpix32d.dll
/usr/lib/codecs/vid_3ivX.xa
/usr/lib/codecs/vid_cvid.xa
/usr/lib/codecs/vid_cyuv.xa
/usr/lib/codecs/vid_h261.xa
/usr/lib/codecs/vid_h263.xa
/usr/lib/codecs/vid_iv32.xa
/usr/lib/codecs/vid_iv41.xa
/usr/lib/codecs/vid_iv50.xa
/usr/lib/codecs/ViVD2.dll
/usr/lib/codecs/vivog723.acm
/usr/lib/codecs/vmnc.dll
/usr/lib/codecs/voxmsdec.ax
/usr/lib/codecs/vp31vfw.dll
/usr/lib/codecs/vp4vfw.dll
/usr/lib/codecs/vp5vfw.dll
/usr/lib/codecs/vp6vfw.dll
/usr/lib/codecs/vssh264core.dll
/usr/lib/codecs/vssh264dec.dll
/usr/lib/codecs/vssh264.dll
/usr/lib/codecs/vsslight.dll
/usr/lib/codecs/vsswlt.dll
/usr/lib/codecs/wma9dmod.dll
/usr/lib/codecs/wmadmod.dll
/usr/lib/codecs/wmsdmod.dll
/usr/lib/codecs/wmspdmod.dll
/usr/lib/codecs/wmv8ds32.ax
/usr/lib/codecs/wmv9dmod.dll
/usr/lib/codecs/wmvadvd.dll
/usr/lib/codecs/wmvdmod.dll
/usr/lib/codecs/wmvds32.ax
/usr/lib/codecs/wnvplay1.dll
/usr/lib/codecs/wnvwinx.dll

```

---

### Post by Rory on 2005-12-11
Drat, copied the files over, using my above command, as you suggested.  Didn't work.  Something wrong with the mplayer plugin playing .ram files.  <scratching head>  

In Firefox, under:
Preferences > Downloads > View Edit Actions, this is what I see:
[IMG]http://www.childwelfare.ca/research/firefoxgrab.png[/IMG]


Can anyone see how the RealPlayer might be prevented from launching, based on this image?  What sucks about this window in Firefox is that while you can change the action for each plugin in the above image and force it to launch from a different app, you don't seem to be able to ADD a new option.  And I'm not seeing a .ram field.  Only .ra fields.

And here is my /usr/lib/mozilla-firefox/plugins directory:

file:///usr/lib/mozilla-firefox/plugins/flashplayer.xpt
file:///usr/lib/mozilla-firefox/plugins/libflashplayer.so
file:///usr/lib/mozilla-firefox/plugins/libjavaplugin.so
file:///usr/lib/mozilla-firefox/plugins/mplayerplug-in-gmp.so
file:///usr/lib/mozilla-firefox/plugins/mplayerplug-in-gmp.xpt
file:///usr/lib/mozilla-firefox/plugins/mplayerplug-in-qt.so
file:///usr/lib/mozilla-firefox/plugins/mplayerplug-in-qt.xpt
file:///usr/lib/mozilla-firefox/plugins/mplayerplug-in-rm.so
file:///usr/lib/mozilla-firefox/plugins/mplayerplug-in-rm.xpt
file:///usr/lib/mozilla-firefox/plugins/mplayerplug-in.so
file:///usr/lib/mozilla-firefox/plugins/mplayerplug-in-wmp.so
file:///usr/lib/mozilla-firefox/plugins/mplayerplug-in-wmp.xpt
file:///usr/lib/mozilla-firefox/plugins/mplayerplug-in.xpt
file:///usr/lib/mozilla-firefox/plugins/nphelix.so
file:///usr/lib/mozilla-firefox/plugins/nphelix.xpt
file:///usr/lib/mozilla-firefox/plugins/nppdf.so


I'm doing my best to provide the clearest, most useful info. :) 

Thanks,
Rory

---

### Post by dcstar on 2005-12-12
[QUOTE=Rory]
......
I'm doing my best to provide the clearest, most useful info. :) 

Thanks,
Rory[/QUOTE]
Try about: plugins  (remove the space after ":") in FF, it may provide more info.

---

### Post by cjazz on 2005-12-12
I had similar problems getting Firefox to use RealPlayer for Real files. I finally was able to do so using the MediaPlayerConnectivity extension.

---

### Post by jkr on 2006-01-04
I managed to get real player working ok in breezy, but then installed mplayer which took over from real player as the embedded plugin for real files;

I got a tip from mozilla forums to remove /usr/lib/mozilla/plugins/mplayerplug-in-rm.so & .xpt files
to somewhere it can't be found -  restart firefox and roberts yer father's brother -  and realplay works fine through firefox!

no disrespect to the mplayer guys, it did work, just getting particlar in me old age
;)

---

### Post by diffuser78 on 2006-01-04
can you play music on this website [www.raaga.com/hindi](www.raaga.com/hindi)

I think I am not able to play because of a realaudio plugin

Can you please help me with this. This is one thing in Ubuntubugging me all the time.

[QUOTE=jkr]I managed to get real player working ok in breezy, but then installed mplayer which took over from real player as the embedded plugin for real files;

I got a tip from mozilla forums to remove /usr/lib/mozilla/plugins/mplayerplug-in-rm.so & .xpt files
to somewhere it can't be found -  restart firefox and roberts yer father's brother -  and realplay works fine through firefox!

no disrespect to the mplayer guys, it did work, just getting particlar in me old age
;)[/QUOTE]

---

### Post by jkr on 2006-01-05
Tried a few of the videos and the player opens HOWEVER
it gets stuck on loading... their help page says:

 "Your media player plug-in may not be working properly.

    * If this problem occurs only occasionally, it is likely due to varying levels of Internet traffic."

I think it is Internet traffic, or to do with raaga hosting, or popup blocker issue not a plugin issue. 

[http://www.raaga.com/channels/hindi/movie/H000902.html](http://www.raaga.com/channels/hindi/movie/H000902.html)
This works ok here.  Once it loads there are scrolling ads in the player, if you have these blocked maybe it won't load properly. 

[http://www.indiaglitz.com/channels/hindi/gallery/events/8791.html](http://www.indiaglitz.com/channels/hindi/gallery/events/8791.html)
work ok, this is a flash plugin however.

Hope that helps ;)

---

### Post by stratotak on 2006-01-05
i tried that web site.raaga...and player lauched..but it just kept saying it was loading..gave up after 2 minutes..and to the original post..have you disabled realtime in mplayer plugin??if you go to say quicktime and view a clip..right click over the video and it will bring up a menu,,find option to not use mplayer for realtime..


just tried the second site..indiaglitz..and it played...

---

### Post by sonytony18 on 2006-01-06
I am facing the exact same problem... raaga.com was working fine in Hoary and no more in Breezy.

i opened the JavaScript console before starting to play a song from the site and received the following errors, maybe they can help figure out what is wrong:

Error: uncaught exception: [Exception... "Component returned failure code: 0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS) [nsIXPCComponents.lookupMethod]"  nsresult: "0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS)"  location: "JS frame :: chrome://global/content/XPCNativeWrapper.js :: anonymous :: line 91"  data: no]

Error: uncaught exception: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIHXPlayer.SetLoop]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: [http://www.raaga.com/playerV31/player_js.asp?mode=3](http://www.raaga.com/playerV31/player_js.asp?mode=3) :: setRaagaSRC :: line 604"  data: no]

Error: uncaught exception: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIHXPlayer.DoStop]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: [http://www.raaga.com/playerV31/player_js.asp?mode=3](http://www.raaga.com/playerV31/player_js.asp?mode=3) :: stop :: line 619"  data: no]

---

