---
title: "No packages with the requested plugins found????? Help?"
date: 2009-05-28
forum: General Help
---

### Post by SchindlerShadow on 2009-05-28
No packages with the requested plugins found
The requested plugins are:

Windows Media Speech decoder

can some1 help? this is on ubuntu 64bit fresh installed all codecs and xine, what did i do wrong? every time i try to play a wmvthis shows up, i press ok, then it plays, but only the vid, no sound, i can play the sample vid fine with sound, whats wrong? it never did this b4!!

in mplayer it says:
Cannot find codec for audio format 0xA

help??? 

any help greatly appreciated!
[IMG]http://img90.imageshack.us/img90/2403/errer.png[/IMG]

---

### Post by michy99 on 2009-05-28
Do you have the w32codecs installed?

---

### Post by SchindlerShadow on 2009-05-28
if it was in synapic, i have it, is their someing in the terminal that i can run to check?

sudo apt-get w32codecs 
E: Invalid operation w32codecs

ps: i can see video, but no sound, btw its Ubuntu 9.04 64bit

---

### Post by michy99 on 2009-05-28
```
sudo apt-get install w32codecs
```

If it is already installed it will tell you. You have to have the Medibuntu repository added to your sources to install it. Have you been through the tutorial here:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by SchindlerShadow on 2009-05-28
> **michy99 said:**
> ```
sudo apt-get install w32codecs
```

If it is already installed it will tell you. You have to have the Medibuntu repository added to your sources to install it. Have you been through the tutorial here:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

still not working, i followed the guide and when i put what you gave me i still get

sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

And I did enable the Medibuntu repository according to the info u gave me...

---

### Post by michy99 on 2009-05-29
Maybe you don't need it for 64 bit. Are you still having they same problem with the audio? The only other suggestion I have is to look at this thread and see if it helps :

[http://ubuntuforums.org/showthread.php?t=1034752](http://ubuntuforums.org/showthread.php?t=1034752)

---

### Post by spcwingo on 2009-05-29
If you're on 64 bit, shouldn't that be:

```
sudo apt-get install w64codecs
```

---

### Post by cariboo on 2009-05-29
To get the w64codecs you will need to enable the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories. Just follow the instructions for your version.

---

### Post by andrew.46 on 2009-05-29
Hi,

I believe that this file is [Windows Media Audio Speech]("http://wiki.multimedia.cx/index.php?title=Windows_Media_Audio_9") which is easily playable by the *32bit* MPlayer and the *32bit* codecs:

```

$ mplayer -ac help | grep 'Windows Media Audio'

wma9dmo     dmo       working   Windows Media Audio 9 DMO  [wma9dmod.dll]
wmadmo      dmo       working   Windows Media Audio DMO  [wmadmod.dll]
[B][COLOR="Purple"]wma9spdmo   dmo       working   Windows Media Audio 9 Speech DMO  [wmspdmod.dll]
wma9spdshow dshow     working   Windows Media Audio 9 Speech DShow  [wmavds32.ax][/COLOR][/B]

```

For example this file:

```
wget http://samples.mplayerhq.hu/A-codecs/WMSP/wmav_8.wma
```

plays with wmspmod.dll:

```

andrew@skamandros~/Desktop$ mplayer wmav_8.wma 
MPlayer SVN-r29325-4.2.4 (C) 2000-2009 MPlayer Team

Playing wmav_8.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 8000 Hz, 1 ch, s16le, 8.0 kbit/6.25% (ratio: 1000->16000)
**[COLOR="Purple"]Selected audio codec: [wma9spdmo] afm: dmo (Windows Media Audio 9 Speech DMO)[/COLOR]**
==========================================================================
AO: [oss] 8000Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  17.3 (17.2) of 17.0 (17.0)  0.5% 

Exiting... (End of file)

```

As for 64bit MPlayer and codecs, I believe that the [64bit codec pack]("http://www.mplayerhq.hu/MPlayer/releases/codecs/essential-amd64-20071007.tar.bz2") will be of little help with wma files:

```

$ tar tjf essential-amd64-20071007.tar.bz2 
essential-amd64-20071007/
[B][COLOR="Purple"]essential-amd64-20071007/cook.so
essential-amd64-20071007/drvc.so
essential-amd64-20071007/sipr.so[/COLOR][/B]
essential-amd64-20071007/README

```

Arguably this is a case where a 32bit system comes out ahead.

Andrew

---

### Post by SchindlerShadow on 2009-05-29
> **spcwingo said:**
> If you're on 64 bit, shouldn't that be:

```
sudo apt-get install w64codecs
```

sudo apt-get install w64codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
w64codecs is already the newest version.
w64codecs set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Help??

PS: if it matters, i installed with the ubuntu 9.04 DVD

---

### Post by spcwingo on 2009-05-29
After some reading, I see that w32 codecs might actually be necessary.  Check out this page:

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Scroll down to the section labeled "Playing Non-Native Media Formats".  This is the part that caught my eye:

> NOTE 3: the w32codecs can be used on amd64 ubuntu (hardy, intrepid) with the i386 mplayer, but it requires manual installation and forcing the install. The i386 mplayer executable can be extracted (and moved or renamed to mplayer32 to keep it separate from the 64 bit version), and will use the ia32 /usr/lib32 entries and w32 codecs - but updated libraries (e.g. libx264.so.59 v.s .57) may also be required.

I do not run the 64 bit version of Ubuntu, so I can't be of further help.  Hopefully someone else who know how to proceed will be able to help you get this done.

---

### Post by SchindlerShadow on 2009-05-29
> **spcwingo said:**
> After some reading, I see that w32 codecs might actually be necessary.  Check out this page:

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Scroll down to the section labeled "Playing Non-Native Media Formats".  This is the part that caught my eye:



I do not run the 64 bit version of Ubuntu, so I can't be of further help.  Hopefully someone else who know how to proceed will be able to help you get this done.

thx, all i need now is some1 who knows and has the 64bit

---

### Post by SchindlerShadow on 2009-06-04
Bump? i still need help!!!

---

### Post by tricolorpoa on 2009-07-15
try to run
```
$ sudo dpkg-reconfigure w64codecs
```

):P

---

