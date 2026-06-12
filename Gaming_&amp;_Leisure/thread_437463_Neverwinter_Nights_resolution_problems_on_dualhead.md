---
title: "Neverwinter Nights resolution problems on dualhead setup"
date: 2007-05-08
forum: Gaming &amp; Leisure
---

### Post by suso on 2007-05-08
I've been having this problem with Neverwinter Nights for a long time and on Ubuntu as well as Gentoo and its probably a bug in X.org or with NWN.  I have a dual head setup.  When I load NWN in full screen it runs at the resolution of my desktop and only gives me the option to change between the resolutions that are available from my desktop screen resolution. When I run nwn in windowed mode, it uses the same resolution as in full screen mode.  When I try to change the width and height settings in nwn.ini, it ignores them.  So I wind up with a window that is mostly on one screen, but half drapes over the other screen.

This is an annoyance because I'd like to have NWN completely on one monitor (one size smaller than the desktop res on that screen) so that I can see everything seamless on one screen and put something like xchat on the other screen. :guitar: 

I've been reading some of the other posts about resolution problems or multimonitor problems with no real solution.  I remember reading somewhere (maybe in the Bioware forums) that this is a known issue with X.  But I can't find that now.  Does anyone have some solution for this?

I'm using the nvidia proprietary drivers and using the twinview option if that makes any difference.  Also, I'm able to play games like ut2004 in windowed mode without having this problem.  Of course ut2004 doesn't really handle two monitors the same way that NWN does.

---

### Post by suso on 2007-05-08
YEAH!  Shortly after I posted this message I thought of just searching for "nwn twinview" on google and low and behold I came across the answer  [here](http://nwn.bioware.com/forums/viewtopic.html?topic=561298&forum=72).

It wasn't quite that simple for me, but after some fiddling :-({|= I was able to make it work.  Now I have NWN running in a 1152x864 window on one screen inside a 1280x1024 screen and the other screen is unobstructed.

:popcorn: 

Here is my Screen section for those that will be helped by this solution:

```
Section "Screen"
      Identifier      "Default Screen"
      Device          "NVIDIA Corporation NVIDIA Default Card"
      Option "TwinView " "on"
      Option "TwinViewOrientation" "RightOf"
      Option "UseEdidFreqs" "True"
     Option "MetaModes" "1280x1024,1280x1024;1280x1024,1024x768;1280x1024,NULL;1152x864,NULL;1024x768,NULL;1280x1024;1280x1024+1200+0"
     Option "HorizSync"   "CRT-0: 30-81;  CRT-1: 30-81"
     Option "VertRefresh" "CRT-0: 56-75;  CRT-1: 56-75"

      Monitor         "SyncMaster"
      DefaultDepth    24
      SubSection "Display"
              Depth           1
              Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
      EndSubSection
      SubSection "Display"
              Depth           4
              Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
      EndSubSection
      SubSection "Display"
              Depth           8
              Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
      EndSubSection
      SubSection "Display"
              Depth           15
              Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
      EndSubSection
      SubSection "Display"
              Depth           16
              Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
      EndSubSection
      SubSection "Display"
              Depth           24
              Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
      EndSubSection
EndSection

```

And here is the display options section of the nwn.ini file:

```
[Display Options]
UseLargeFont=0
RefreshRate=0
BitsPerPixels=32
Height=864
Width=1152
TexturePack=3
FullScreen=0
AllowWindowedMode=1

```

Now I'm happy.   :guitar: :guitar:  :guitar: :guitar: :guitar: :guitar:

---

### Post by zaf on 2007-05-12
[http://ubuntuforums.org/showthread.php?t=416249]("http://ubuntuforums.org/showthread.php?t=416249") has a solution that puts OpenGL programs (such as Neverwinter Nights) in one Window when in full screen mode, thus not centering in the middle spanning two screens.

Unfortunately it doesn't allow you to see another program running in the unused Window. This is because it is taking place at Full Screen mode. Your solution obviously does allow this, but I personally find that games run slower when in Windowed mode, hence the reason for posting the above solution.

---

