---
title: "RealMedia files wont play???"
date: 2009-02-18
forum: General Help
---

### Post by casmok on 2009-02-18
Hi,

I'm trying to view some online videos. The website says you need Real Player to view them. 

So to in order to use Mplayer in Hardy I went to Medibuntu. I downloaded/installed the W64Codecs package Medibuntu says are necessary to play non native formats such as Real, Quicktime etc. 

Now when I try to view the videos it still wont work and I get the error message "GstDecodeBin: This appears to be a text file"

Any ideas?

Thanks
MIke

---

### Post by mb_webguy on 2009-02-18
You can try installing [RealPlayer]("http://www.real.com/linux")...

---

### Post by jerome1232 on 2009-02-18
You could also install helix-player which is the engine real player is based on.
```
sudo apt-get install helix-player
```

If you have the medibuntu repo's realplayer 10 is avaible from their repos.

```
sudo apt-get install realplayer
```

---

### Post by solwic on 2009-02-18
> **jerome1232 said:**
> You could also install helix-player which is the engine real player is based on.
```
sudo apt-get install helix-player
```

If you have the medibuntu repo's realplayer 10 is avaible from their repos.

```
sudo apt-get install realplayer
```

Medibuntu works for me.  I don't install the player, just the codecs.  It lets MoviePlayer play .rm files.

---

### Post by jerome1232 on 2009-02-18
> **jrock612 said:**
> Medibuntu works for me.  I don't install the player, just the packages.  It lets MoviePlayer play .rm files.

What packages exactly?

---

### Post by solwic on 2009-02-18
> **jerome1232 said:**
> What packages exactly?

Well maybe I am installing the player, but I might be defining "player" differently.  I use MoviePlayer to watch .rm files after going through the steps [here.]("https://help.ubuntu.com/community/Medibuntu")

Nothing ever comes up and says, "RealPlayer" though.  I double click an .rm file and it opens, as I said, in MoviePlayer.

Is that what you meant?

---

### Post by jerome1232 on 2009-02-18
Ah So your saying after installing w32codecs or w64codecs the rm files work for you? Good to know I wasn't sure if those allowed rm files to play.

The only reason I suggested the players themselves was because the op already tried that (installing w64codecs) and it's still not working.

---

### Post by solwic on 2009-02-18
> **jerome1232 said:**
> Ah So your saying after installing w32codecs or w64codecs the rm files work for you? Good to know I wasn't sure if those allowed rm files to play.

The only reason I suggested the players themselves was because the op already tried that (installing w64codecs) and it's still not working.

Ah...I didn't realize it was 64bit.  Yes, all I install is the w32codecs.  They work fine on a 32bit system.  

Sorry for the mix up.

---

### Post by casmok on 2009-02-19
> **jrock612 said:**
> Ah...I didn't realize it was 64bit.  Yes, all I install is the w32codecs.  They work fine on a 32bit system.  

Thanks. Sorry for the mix up.

I should have been more specific. The files I'm trying which is just on one site for now, are .ram

Helix player might be an option if I cant get them to go under Mplayer which I'd prefer to do and was assured could handle then with the W64codecs.

---

### Post by casmok on 2009-02-19
I'm just wondering, is there something I can enter in terminal to check the W64codecs are properly installed?

---

### Post by andrew.46 on 2009-02-19
Hi casmok,

> **casmok said:**
> I'm just wondering, is there something I can enter in terminal to check the W64codecs are properly installed?

Well MPlayer can show you specific codecs. For example video codecs with the name 'real':

```

andrew@skamandros~$ [COLOR="Red"]**mplayer -vc help | grep -i real**[/COLOR]
rv3040      realvid   problems  Linux RealPlayer 10 RV30/40  [drvc.so]
rv3040win   realvid   working   Win32 RealPlayer 10 RV30/40  [drvc.dll]
rv40        realvid   working   Linux RealPlayer 9 RV40  [drv4.so.6.0]
rv40win     realvid   working   Win32 RealPlayer 9 RV40  [drv43260.dll]
rv40mac     realvid   working   Mac OS X RealPlayer 9 RV40  [drvc.bundle/Contents/MacOS/drvc]
rv30        realvid   working   Linux RealPlayer 8 RV30  [drv3.so.6.0]
rv30win     realvid   working   Win32 RealPlayer 8 RV30  [drv33260.dll]
rv30mac     realvid   working   Mac OS X RealPlayer 9 RV30  [drvc.bundle/Contents/MacOS/drvc]
rv20        realvid   working   Linux RealPlayer 8 RV20  [drv2.so.6.0]
rv20winrp10 realvid   working   Win32 RealPlayer 10 RV20  [drv2.dll]
rv20win     realvid   working   Win32 RealPlayer 8 RV20  [drv23260.dll]
rv20mac     realvid   working   Mac OS X RealPlayer 9 RV20  [drv2.bundle/Contents/MacOS/drv2]
fraps       vfw       working   FRAPS: Realtime Video Capture  [frapsvid.dll]

```

Similar for audio codecs:

```

andrew@skamandros~$ [COLOR="Red"]**mplayer -ac help | grep -i real**[/COLOR]

ffra144     ffmpeg    working   FFmpeg RealAudio 1.0  [real_144]
ffra288     ffmpeg    working   FFmpeg RealAudio 2.0  [real_288]
ra144       realaud   working   RealAudio 1.0  [14_4.so.6.0]
ra144win    realaud   working   Win32 RealAudio 1.0  [14_43260.dll]
ra144mac    realaud   working   Mac OS X RealAudio 1.0  [14_4.shlb]
ra288       realaud   working   RealAudio 2.0  [28_8.so.6.0]
ra288win    realaud   working   Win32 RealAudio 2.0  [28_83260.dll]
ra288mac    realaud   working   Mac OS X RealAudio 2.0  [28_8.shlb]
ra10cook    realaud   working   RealPlayer 10 COOK audio  [cook.so]
racook      realaud   working   RealAudio COOK  [cook.so.6.0]
ra10cookwin realaud   working   Win32 RealAudio 10 COOK  [cook.dll]
racookwin   realaud   working   Win32 RealAudio COOK  [cook3260.dll]
racookmac   realaud   working   Mac OS X RealAudio COOK  [cook.bundle/Contents/MacOS/cook]
rasipr      realaud   working   RealAudio Sipro  [sipr.so.6.0]
ra10sipr    realaud   working   RealPlayer 10 RealAudio Sipro  [sipr.so]
ra10siprwin realaud   working   Win32 RealAudio 10 Sipro  [sipr.dll]
rasiprwin   realaud   working   Win32 RealAudio Sipro  [sipr3260.dll]
rasiprmac   realaud   working   Mac OS X RealAudio Sipro  [sipr.bundle/Contents/MacOS/sipr]
raatrc      realaud   working   RealAudio ATRAC3  [atrc.so.6.0]
ra10atrc    realaud   working   RealPlayer 10 RealAudio ATRAC3  [atrc.so]
ra10atrcwin realaud   working   Win32 RealAudio 10 ATRAC3  [atrc.dll]
raatrcwin   realaud   working   Win32 RealAudio ATRAC3  [atrc3260.dll]
raatrcmac   realaud   working   Mac OS X RealAudio ATRAC3  [atrc.bundle/Contents/MacOS/atrc]

```

How cool is MPlayer :-).

Andrew

---

### Post by casmok on 2009-02-19
> **andrew.46 said:**
> Hi casmok,



Well MPlayer can show you specific codecs. For example video codecs with the name 'real':



How cool is MPlayer :-).

Andrew

Thanks!
Hmmmm Well I've got the codecs OK. But absolutely nothing will play. Anything I try says it's "not yet supported" 
Any ideas?? :confused:
Mike

---

### Post by casmok on 2009-02-19
OK I've messed around a bit more with this and tried another site which prompted and searched/installed for plugins.

What I now added beyond MPlayer is:

W64codecs  from Medibuntu
Gstreamer extra plugins (the ugly set)
Mplayer plugin for Mozilla

Now when I try to play my original video the Mplayer plugin embedded player launches but then stops. Is there anything else I should be installing?

---

